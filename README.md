# scraper api free: What ScraperAPI's 5,000-Credit Trial and Permanent Free Plan Actually Get You (And When It's Worth Paying)

Short answer up front: yes, you can use ScraperAPI for free, and you actually get two free things at once. Sign up and you receive a **7-day trial with 5,000 API credits** plus a **permanent free plan with 1,000 credits per month** — no credit card required for either. The catch that most articles skip: credits aren't 1:1 with pages. Scraping Amazon costs 5 credits per request, Google SERP costs 25, and combining JS rendering with an ultra-premium proxy burns 75 credits in a single call. That math determines whether the free tier is enough for you or whether you should plan to pay from day one.

This article walks through exactly what the free tier includes, what it can and can't scrape, the full paid plan lineup, and the credit-cost details that trip up most new users.

> **Quick take:** Most people testing ScraperAPI should start with the free trial's 5,000 credits, run their real target sites through it, and check the `sa-credit-cost` response header to see what each request actually costs. If your targets are plain HTML pages, the permanent 1,000-credit free plan may be all you ever need at $0. Heavy Amazon or Google scraping? You'll want a paid plan quickly.
>
> 👉 [Claim your free API key with 5,000 trial credits — no credit card needed](https://www.scraperapi.com/signup?fp_ref=coupons)

## What You Actually Get for Free

ScraperAPI's free tier is really two overlapping offers, and knowing the difference saves you from a common surprise: your credits suddenly dropping from 5,000 to 1,000 after a week.

|  | 7-Day Trial | Permanent Free Plan |
| --- | --- | --- |
| Credits | 5,000 (one-time) | 1,000 per month |
| Duration | 7 calendar days from signup | Ongoing |
| Credit card | Not required | Not required |
| Concurrent threads | 5 | 5 |
| Geotargeting | Limited | Limited |
| Ultra-premium proxies | Not available | Not available |

The trial credits stack on top of the free plan, so day one gives you 5,000 to work with. When the trial ends, you settle into the 1,000/month rhythm. Neither option requires a credit card, and registration takes under five minutes: email and password, confirm the link, copy your API key from the dashboard's "Manage API keys" section, and send your first request.

Both free tiers include the core engine — rotating residential and datacenter proxies across 50+ countries, automatic CAPTCHA handling, headless-browser JavaScript rendering, and automatic JSON parsing. What they exclude matters more: ultra-premium proxies are paid-plan only, and geotargeting is restricted compared to Business and above.

One genuinely useful detail: failed requests don't cost credits. ScraperAPI only charges for successful responses — HTTP 200 or 404. Everything else is free, so you can hammer a target that's blocking you without draining your allowance.

## ScraperAPI Plans and Pricing (All Current Plans)

Here's the complete lineup from ScraperAPI's pricing page. Annual billing takes 10% off automatically, no promo code needed.

| Plan | Monthly Price | Annual (per month) | Credits/mo | Threads | Get Started |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | — | 1,000 | 5 | [Start free](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Hobby | $49 | $44.10 | 100,000 | 20 | [Start Hobby trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [Start Startup trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [Start Business trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [Start Scaling trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [Start Professional trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [Start Advanced trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22M+ | 500+ | [Talk to sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Every paid plan bundles the same core stack: JS rendering, premium proxies, CAPTCHA and anti-bot detection, custom sessions, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. The pricing page marks Scaling as the most popular plan, and it's also the cheapest tier that includes pay-as-you-go overage — more on why that matters below.

If you pay and change your mind, third-party reviews report a 7-day refund window on paid plans. Combined with the free trial, that would give you two no-cost ways to evaluate the service before any money sticks — though it's worth confirming the current terms with support before counting on it.

## The Credit System: Why "100,000 Credits" Isn't 100,000 Pages

This is the part most free-trial guides gloss over, and it's the single most important thing to understand before you pick a plan.

A standard HTML page costs 1 credit. Beyond that, ScraperAPI charges by target site and by feature flags:

- **Amazon, eBay, Walmart:** 5 credits per request
- **Google and Bing SERPs (including subdomains):** 25 credits per request
- **LinkedIn:** 30 credits per request
- **Sites behind Cloudflare, DataDome, or PerimeterX:** +10 credits when the bypass triggers, detected automatically
- **`render=true` (JS rendering), `premium=true`, `screenshot=true`:** +10 each
- **`ultra_premium=true`:** +30, paid plans only

Here's the trap: combinations cost more than the sum of their parts. Premium proxy plus JS rendering is 25 credits, not 20. Ultra-premium plus rendering is 75, not 40. On a $49 Hobby plan with 100,000 credits, that 75-credit combo means roughly **1,333 scrapes** — while the same plan yields the full 100,000 pages on simple, unprotected HTML. Same plan, two completely different realities.

You can protect yourself with two built-in tools. The dashboard's Domain Cost Estimator shows the exact credit cost for any URL before you scale up, and there's a programmatic endpoint (`api.scraperapi.com/account/urlcost?...`) that returns the cost for a specific URL-and-parameter combo — handy if you're building automation that needs to budget credits dynamically. You can also set a `max_cost` per request to cap what any single scrape can spend. And for direct verification, every API response includes a `sa-credit-cost` header showing what that request actually consumed. Check it during your free trial and you'll know your true burn rate before spending a dollar.

If you'd rather see the official breakdown side by side before running the numbers yourself, 👉 [view the full plan comparison and current credit pricing](https://www.scraperapi.com/pricing/?fp_ref=coupons).

## Hidden Limits That Affect the Free Tier (And Which Plan Fixes Each)

Several restrictions live in the documentation rather than on the pricing page. They won't show up in a comparison table, but each one can end a project.

**Geotargeting.** Country-level targeting outside the US and EU starts at Business ($299/mo). Free plan, trial, Hobby, and Startup are limited to US and EU locations. If your project needs localized results from other regions, factor that into your budget from the start.

**Pay-as-you-go overage.** Only Scaling and above can keep scraping past their monthly credit allowance at a fixed per-credit rate. On Hobby, Startup, and Business, running out mid-month means upgrading a plan or waiting for renewal — requests pause until credits reset. (Alternatively, auto-upgrade is opt-in on Hobby through Professional and moves you to the next plan automatically.)

**Concurrency.** Exceeding your thread limit returns a 429 error and the request is rejected outright — not queued. Five concurrent threads on the free tier means five requests in flight, period.

**Analytics history.** Hobby and Startup only keep 30 days of usage analytics. Business and up give you unlimited history. Minor for most, relevant if you need long-term usage auditing.

**Other fine-print items worth knowing:**
- 404 responses consume credits (they count as "successful"), and cancelled requests are charged if you cancel before the 70-second processing window completes
- Difficult targets carry a forced 10-minute cache, so time-sensitive data like live pricing can be up to 10 minutes stale
- There are no proactive low-credit alerts — no email, no SMS. Check the dashboard manually, or set a calendar reminder during your first month
- The no-code DataPipeline product uses its own, higher credit schedule (a 1-credit standard request costs 6 credits there)
- Login-required sites are off-limits under the terms of service; session persistence is supported, but scraping behind auth walls is not

One practical tip from the documentation: set a 70-second timeout in your application when targeting hard-to-scrape domains. Skipping this is the most common reason new accounts see failed first-day requests.

## When the Free Tier Is Enough — and When It Isn't

The permanent 1,000-credit monthly plan fits a narrow but real set of use cases:

- **A personal price-monitoring script** checking a handful of Amazon products daily — roughly 200 requests a month at the 5-credit rate, well under the cap
- **A weekly SERP tracking run** of 30–40 keywords, one pull each per month — about 1,000 credits, tight but workable
- **Hobby data collection** from plain-HTML sources: blogs, news sites, public records, simple catalogs — the full 1,000 scrapes at the base rate
- **API evaluation** — a permanent sandbox to test ScraperAPI against your targets before committing

What the free tier handles badly: anything needing ultra-premium proxies, geotargeting beyond the defaults, more than 5 concurrent threads, or any single heavy job. A batch of ultra-premium-plus-rendering requests — 75 credits each on a paid plan — simply can't run here at all, and even ordinary heavy jobs can eat a month's allowance in an afternoon.

If you're comparing options on a free budget, the landscape as of mid-2026 looks like this: ScrapingBee's Freelance plan runs $49/month for 250,000 credits with 10 concurrent requests — a larger raw credit allocation than ScraperAPI's Hobby plan at the same price. Zyte offers a $5 free credit with usage-based pricing from about $0.06 per 1K pages. Oxylabs provides a 2,000-result free trial at $0.25 per 1K results, and Bright Data's pay-as-you-go model runs $1.50 per 1K records with 5,000 free records monthly. ScraperAPI's 5,000-credit trial is among the most generous no-card trials in this group, and its credit system is transparent once you know where to look — though raw credit volume at the $49 tier is one dimension where a competitor publishes a bigger number.

## Frequently Asked Questions

**Is ScraperAPI really free?**
Yes, two ways: a permanent free plan with 1,000 credits per month (5 concurrent threads), and a 7-day trial that adds 5,000 one-time credits on top. Neither requires a credit card.

**How many pages can I scrape for free?**
Depends entirely on your targets. 1,000 monthly credits equals 1,000 plain HTML pages, 200 Amazon product requests, or 40 Google SERP pulls. The 75-credit ultra-premium + rendering rate is a paid-plan figure — the free tier can't use ultra-premium proxies at all. Check the `sa-credit-cost` header or the Domain Cost Estimator to see which category your targets fall into.

**Do failed requests cost credits?**
No. Only HTTP 200 and 404 responses are charged. Requests that fail outright don't consume your allowance. Note that 404s do count as billable, though.

**What happens if I run out of credits?**
On the free plan, scraping pauses until credits renew. On Hobby through Professional you can opt into auto-upgrade; on Scaling and above, pay-as-you-go keeps requests running at a fixed per-credit rate up to a monthly cap you set.

**Do I need a promo code for a discount?**
No — annual billing applies a 10% discount on every plan automatically. Some third-party reviews mention a first-month discount code, but it isn't confirmed on the official pricing page, so treat annual billing as the reliable discount.

**Is there a refund if I pay and don't like it?**
Independent reviews report a 7-day refund window on paid plans, which would stack with the free trial for two no-cost evaluation periods. Since this isn't spelled out on the public pricing page, confirm the current policy with support before purchasing.

## Which ScraperAPI Plan Should You Pick?

Working through it by scenario:

- **Just exploring, or running a small monitoring script** → stay on the free plan. 1,000 credits/month at $0 covers modest plain-HTML work indefinitely.
- **Testing whether ScraperAPI can handle your specific targets** → burn the 5,000 trial credits on your real sites first, verify costs via the `sa-credit-cost` header, then decide. No card needed.
- **Regular scraping of simple HTML at moderate volume** → Hobby at $49/month ($44.10 annual) is the sensible entry point; 100,000 base-rate pages is real capacity if you're not touching protected sites.
- **Amazon or e-commerce monitoring with JS-heavy pages** → do the math first. At 5+ credits per request (more with rendering), Startup or Business gives you headroom without constant credit anxiety.
- **Google SERP tracking at any scale** → 25 credits per pull adds up fast; Business ($299/mo) is where country-level geotargeting also unlocks, which SERP work usually needs.
- **Production workloads where running dry mid-month is unacceptable** → Scaling ($475/mo) is the cheapest tier with pay-as-you-go overage, which is likely why the pricing page flags it as the most popular plan.

Two things to confirm before you click buy: that your target sites don't require login (that's against the terms of service), and that your expected monthly burn rate fits the credit tier — the Domain Cost Estimator in the free dashboard will tell you exactly what your workload costs.

Ready to test it against your own targets? 👉 [Start the free trial and get your first 5,000 credits without entering a card](https://www.scraperapi.com/signup?fp_ref=coupons)
