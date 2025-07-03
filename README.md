🧠 Run Ollama in Docker (with automatic model loading)
✅ Requirements
Docker and Docker Compose installed

curl or a similar HTTP client installed

🚀 Step 1: Start Ollama with a model via Docker Compose

Then simply start the container:

docker compose up -d
📦 The model llama3 will be automatically pulled on the first run.

You can verify that the API is up and running with:
curl http://localhost:11434

Expected response:
{"status":"OK"}

Here’s an example of sending a prompt to the model:
curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "Hi! Tell me an interesting fact.",
  "stream": false
}'

Expected response:
{
  "response": "An interesting fact: octopuses have three hearts...",
  "done": true
}

🔁 Optional: Continuing the conversation

You can pass the context from a previous response to maintain conversation history:
"context": [ ... ]

🔄 Switching or updating the model

To switch to another model:

Change the model name in the OLLAMA_MODELS variable:
environment:
  - OLLAMA_MODELS=mistral
