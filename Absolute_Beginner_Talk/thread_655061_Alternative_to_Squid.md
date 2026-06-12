---
title: "Alternative to Squid?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by SynapseKDE on 2007-12-31
Hello all.

I am new to linux and I was wondering if theres any application that could help me make a better use of my bandwidth. I have read somewhere that Squid, as a proxy, could store webpages, that way the pages wouldnt have to be 'downloaded' all over again each time I opened them.

I tried to configure Squid but, given my level of knowledge on computers (-_-), I find it rather complex. Is there an easier alternative to accomplish the task of caching my web pages, something more 'begginer friendly'?

---

### Post by Cypher on 2007-12-31
I think caching proxies are a waste in today's landscape of dynamic websites. Very few pages these days have static content, so any caching proxy you setup will be constantly downloading new content to show to you. So I don't think, in the end, you're going to be saving any bandwidth.

If you have DSL or Cable modem, you shouldn't even worry about bandwidth as no ISP rate limits..yet..

---

### Post by OfficeLinebacker on 2008-01-27
> **Cypher said:**
> I think caching proxies are a waste in today's landscape of dynamic websites. Very few pages these days have static content, so any caching proxy you setup will be constantly downloading new content to show to you. So I don't think, in the end, you're going to be saving any bandwidth.

If you have DSL or Cable modem, you shouldn't even worry about bandwidth as no ISP rate limits..yet..

Isn't there a small advantage when talking about the individual elements of a page, like the gifs for button images/headers/etc?  For example when you browse a site like newegg where many of the images near the top/bottom/sides of the page are the same, it's only the middle parts with the content that changes.

Or are those individual images generally cached locally by modern web browsers, rendering caching proxies moot?

---

