# GenAI Architect - Azure OpenI + Langfuse
# 📈 Market Sentiment Analyzer using LangChain + Azure OpenAI + Langfuse

This project builds a real-time pipeline that:
- Accepts a company name (e.g., "Microsoft")
- Extracts the stock symbol (e.g., MSFT)
- Fetches recent news headlines from Yahoo Finance
- Analyzes sentiment using Azure OpenAI's GPT-4o via LangChain
- Logs and traces execution using Langfuse
- Outputs a structured JSON object

---

## Setup Instructions

### 1. Clone or Download the Repository
```bash
git clone https://github.com/<your-username>/market-sentiment-analyzer.git
cd market-sentiment-analyzer
```

### 2. Install Required Packages
Ensure Python 3.10+ is installed.

```bash
pip install -U langchain langchain-community openai langfuse yfinance python-dotenv
```

### 3. Setup `.env` File
Create a `.env` file in the root folder or upload via Google Colab.

Example:
```env
OPENAI_API_KEY=your-openai-api-key
OPENAI_ENDPOINT=https://your-resource-name.openai.azure.com/
DEPLOYMENT_NAME=gpt-4o-mini
OPENAI_API_VERSION=2024-05-01

LANGFUSE_PUBLIC_KEY=your-langfuse-public-key
LANGFUSE_SECRET_KEY=your-langfuse-secret-key
LANGFUSE_HOST=https://cloud.langfuse.com
```

---

## Azure OpenAI API Setup

1. Go to [https://portal.azure.com](https://portal.azure.com)
2. Create a **Cognitive Services - Azure OpenAI** resource
3. Deploy a model (e.g., GPT-4o, gpt-35-turbo)
4. Copy the:
   - **Endpoint**
   - **Deployment name**
   - **API key**
   - **API version**

---

##Langfuse Setup

1. Go to [https://cloud.langfuse.com](https://cloud.langfuse.com)
2. Create a project (e.g., `Sentiment-Analyzer`)
3. Go to **Settings > API Keys**
4. Copy your:
   - **Public Key**
   - **Secret Key**
   - **Host** (default: `https://cloud.langfuse.com`)

---

## How to Run the Chain

### Run in Notebook or Script:
```python
company = "Microsoft"
newsdesc, ticker = get_news_summary(company)
result = analyze_sentiment(newsdesc, company, ticker)

print(result.model_dump_json(indent=2))
```

---

## Sample Output
```json
{
  "company_name": "Microsoft",
  "stock_code": "MSFT",
  "newsdesc": "Microsoft announces new AI features...",
  "sentiment": "Positive",
  "people_names": ["Satya Nadella"],
  "places_names": ["Redmond"],
  "other_companies_referred": ["OpenAI"],
  "related_industries": ["Cloud", "Software", "AI"],
  "market_implications": "Stock likely to trend higher",
  "confidence_score": 0.94
}
```

---

## Safety Notes
- Do **NOT** commit your actual `.env` file
- Use `.env.template` for sharing keys safely
- You may add `.env` to `.gitignore`

---

## Bonus Ideas
- Use Wikipedia API for entity linking
- Plot sentiment trends over time using Matplotlib
- Use LangChain's `MultiPromptChain` for diverse news types

---


