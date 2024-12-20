FROM node:20-slim

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application files
COPY . .

# Create a .env file with the API key from build arg
RUN echo "VITE_GEMINI_API_KEY=$VITE_GEMINI_API_KEY" > .env

# Build the frontend
RUN npm run build

# Set production environment
ENV NODE_ENV=production
ENV PORT=8080

# Expose the port
EXPOSE 8080

# Start the server
CMD ["node", "--env-file=.env", "server/index.mjs"]