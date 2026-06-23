# Bitovi-Blog-Rag-Agent

An intelligent AI agent built with n8n that answers questions about Bitovi's blog content using Retrieval-Augmented Generation (RAG).

## Overview

This workflow creates an AI-powered chatbot that can answer questions like:
- "What is Bitovi's latest blog post about?"
- "Can you show me all Bitovi articles about DevOps?"
- "How many articles does Bitovi have about AI?"
- "What kind of tools does Bitovi recommend for E2E testing?"

## Architecture

**Data Ingestion Pipeline**
- Automated scraping of all Bitovi blog articles
- Content extraction and cleaning
- Metadata preservation (titles, authors, dates, categories)
- Vector embeddings generation using Google Gemini
- Storage in Pinecone vector database

**AI Agent with RAG**
- Real-time question processing through chat interface
- Vector similarity search for relevant content retrieval
- Context-aware response generation with Google Gemini
- Source attribution with direct links to original articles

## Technical Implementation

### Prerequisites
```bash
- N8N self-hosted instance
- Google Gemini API key
- Pinecone API account
- Webhook URL for chat interface
```

### Installation Steps

1. **Import Workflow**
   ```bash
   # Import the provided JSON file into n8n
   # File: bitovi-blog-ai-agent.json
   ```

2. **Configure Credentials**
   - Add Google Gemini API credentials
   - Add Pinecone API credentials
   - Set up webhook for chat interface

3. **Initialize Data Pipeline**
   - Activate the schedule trigger for automatic blog scraping
   - Manual execution will index all existing articles
   - Subsequent runs capture new content automatically

4. **Test Chat Interface**
   - Send test queries through the webhook endpoint
   - Verify responses include relevant content and source links

### Workflow Components

**Data Collection (Automated)**
```
Schedule Trigger → Page Scraping → Content Extraction → 
HTML Cleaning → Vector Embedding → Pinecone Storage
```

**Question Answering (Real-time)**
```
Chat Trigger → AI Agent → Vector Retrieval → 
Response Generation → Source Attribution
```

## Key Features

- **Comprehensive Coverage**: Ingests all Bitovi blog articles automatically
- **Smart Retrieval**: RAG pipeline with top-500 relevant results
- **Accurate Responses**: Grounded in actual blog content only
- **Source Tracking**: Every response includes original article links
- **Conversation Memory**: Maintains context across chat sessions
- **Error Handling**: Robust processing with failure recovery
- **Auto-Updates**: Scheduled content refresh for new articles

## Response Format

```
Relevant information extracted from Bitovi blogs
Read more in https://www.bitovi.com/blog/article-url
```

## Performance Metrics

- **Content Processing**: 800 items per batch
- **Retrieval Speed**: Sub-second response times
- **Coverage**: All historical and new blog posts
- **Accuracy**: Responses grounded only in blog content
- **Reliability**: Continuous operation with error recovery

## Demonstration Capabilities

The AI agent successfully handles various query types:

**Latest Content Queries**
- Identifies most recent blog posts by publication date
- Provides summaries with direct links

**Category-Based Searches**
- Filters articles by topic (DevOps, AI, testing, etc.)
- Lists relevant articles with metadata

**Quantitative Questions**
- Counts articles by category or topic
- Provides statistical insights about blog content

**Tool Recommendations**
- Extracts specific tool mentions from articles
- Contextualizes recommendations with source attribution
