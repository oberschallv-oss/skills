---
name: wsj-briefing
description: Curates a WSJ technology briefing from WSJ's public RSS feed (headlines + summaries only, since wsj.com article pages are blocked). Use when Victor asks for his WSJ briefing or tech news curation.
---

You are curating today's WSJ technology briefing for Victor. Be rigorous and concise.

FEED: https://feeds.a.dj.com/rss/RSSWSJD.xml
(Optional, if Victor asks for broader coverage, merge these too and dedupe: Markets https://feeds.a.dj.com/rss/RSSMarketsMain.xml, Business https://feeds.a.dj.com/rss/WSJcomUSBusiness.xml, World https://feeds.a.dj.com/rss/RSSWorldNews.xml, Opinion https://feeds.a.dj.com/rss/RSSOpinion.xml)

STEPS:
1. Fetch the feed above. It returns recent WSJ articles as <item> blocks with <title>, <link>, <description>, <pubDate>. Do NOT attempt to fetch the wsj.com article URLs themselves - that domain is blocked and will fail. Work only from the title + description in the feed.
2. Parse all items. Drop anything older than 48 hours by pubDate.
3. Curate down to the 6-8 most significant stories. Rank by:
   - Material business/market impact (funding, M&A, earnings, regulation)
   - AI / semiconductor / cloud infrastructure developments
   - Anything signaling a strategic shift at a major tech company
   Deprioritize: product reviews, opinion, incremental updates.
4. Output a markdown briefing:
   - One line per story: **headline** - 1-2 sentence why-it-matters in your own words (paraphrase the description, don't copy it), then the WSJ link in parentheses so Victor can open it (he has a WSJ subscription and can read the full article).
   - Group under: "Top Stories" (3-4) and "Also Notable" (the rest).
   - Lead with the single most consequential item.
5. End with a 2-line "Thread to watch" call: the one story most likely to develop further this week, and why.

Keep it tight. No preamble. If the feed returns nothing or fails to parse, say so and stop - don't substitute other sources.
