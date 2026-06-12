---
title: "Web 2.0"
date: 2007-01-12
forum: Art &amp; Design
---

### Post by jessewryan on 2007-01-12
I was just wondering if anyone could give me a little shove in the right direction as to how I could go about creating a website with a web 2.0 look and feel. Also I was wondering how to create an RSS feed for my mainpage. If anyone could let me know that would be great. Thanks.

---

### Post by finer recliner on 2007-01-12
web 2.0 look and feel is unfortunatily a very vague description.

make a list of different features you want and then go research them individually (example: i want to be able to click "reply" and a new window to type text will appear without having to refresh the page, as seen in gmail, is very common)

also start researching AJAX (asyncronous Javascript and XML)

---

### Post by jessewryan on 2007-01-12
Alright, I was meaning things like syndication and transparency. More of the design aspect as opposed to the programming aspect. But thanks for the reply.

---

### Post by jem7v on 2007-01-12
1. Define Web 2.0.  Do you mean shiny with plastic buttons, or something else?  I wasn't aware syndication was a visual style... And what do you want transparent?
2. [http://www.w3schools.com/rss/rss_intro.asp](http://www.w3schools.com/rss/rss_intro.asp) has, in the past, been a useful site for web design for me.

P.S. Google is probably a better place to look for web design tips than the Ubuntu forums.

---

### Post by ButteBlues on 2007-01-12
RSS is simply some fancy XML. Here's a sample rss.xml file:

```
<?xml version="1.0" encoding="utf-8"?>
	<rss version="2.0">
		<channel>
			<title>Title of your feed</title>
			<link>Link to your site</link>
			<description>Description of your feed</description>

<!-- You need to edit this each time you update. Follow this format: DDD, dd mmm yyyy HH:mm:ss TMZ-->

			<lastBuildDate>12 Jan 2007 00:01:00 CST</lastBuildDate>

<!-- Don't edit this. -->

			<language>en-us</language>


<!-- This is where you add each article. -->

<item>
<title>Article title</title>
<link>Link to Article</link>
<guid>Link to Article</guid>
<pubDate>Date Article was Published</pubDate>
<description>Description of the article.</description>
</item> 
```

That's of course, if you do it manually. Most PHP-based CMSs these days offer built in RSS support.

---

### Post by airtonix on 2007-01-14
drupal with jquery.  boooyah!  version 5 rc2 is available now.

---

