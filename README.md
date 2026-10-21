# ⭐ Shopify Amazon-Style AI Review Summary Section (OS 2.0)

A lightweight Shopify Online Store 2.0 section inspired by Amazon's AI-generated customer review takeaways. Summarizes sentiment, key product highlights, and sizing recommendations directly on product pages.

---

## 🏗️ Architecture: Why Pre-Computed AI vs. Live LLM?

A common anti-pattern in e-commerce is trying to query an LLM (OpenAI/Claude) live on every page load. In production, this causes two major issues:
1. **Performance Drag:** Real-time AI generation adds 2–4 seconds of latency, destroying Core Web Vitals and conversion rates.
2. **API Costs:** 50,000 monthly store visitors would translate into tens of thousands of redundant API calls.

### The Production Approach Used Here:
This section uses the **async pre-computed pattern**:
- An automated workflow (Shopify Flow, Webhook, or script) passes accumulated reviews to an LLM once.
- The resulting summary and sentiment pills are written to **Shopify Product Metafields** (`product.metafields.custom.ai_summary`).
- This section renders that data **statically and instantaneously (0ms added latency)** directly within the theme.

---

## 🎯 Conversion Value
- **Instant Social Proof:** Gives shoppers an immediate 5-second takeaway without scrolling through 50+ reviews.
- **Reduces Returns:** Clear feedback badges (e.g., *"Runs Slightly Slim"*) set expectations upfront.
- **Zero App Fees:** Operates natively inside the theme without recurring monthly app costs.

---

## 🛠 Installation
1. Add `sections/ai-review-summary.liquid` to your theme's `/sections` folder.
2. In the Shopify Customizer on any **Product Template**, click **Add section** $\rightarrow$ **AI Review Highlights**.
3. Map the fields to your custom Product Metafields or configure static fallback copy in the theme settings.
