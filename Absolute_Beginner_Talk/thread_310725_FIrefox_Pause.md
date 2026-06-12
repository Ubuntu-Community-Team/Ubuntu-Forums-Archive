---
title: "FIrefox Pause"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-01
Hei all,

Just a quick query, when using firefox, it has a distinct pause before it loads a web page - up to 6 or 7 seconds, once it starts it is very quick. I have 10 mbit connection, so it shouldnt be that. anyway to speed this up?

---

### Post by mushroom on 2006-12-01
It's a weird quirk. I haven't been able to solve it myself, but someone else may have a solution. Here's a temporary one: If you're using KDE, you can use Opera; if you're using GNOME, you can use Epiphany (sudo apt-get install epiphany-browser epiphany-extensions) which behaves much like Firefox and has many of its extensions (including adblock/filterset.g and Greasemonkey).

---

### Post by SyvanX on 2006-12-01
Check your DNS settings, the problem might be there.  If you're dual booting, make sure they're the same as your windows settings.  Is your problem just firefox?

---

### Post by tchoklat on 2006-12-01
check that you not using a proxy which can slow things down - also do you have a cache that is being accessed first. This is the case at my work on our 10mBit connection
 
 
Tony

---

### Post by Jussi01 on 2006-12-02
> **mushroom said:**
> It's a weird quirk. I haven't been able to solve it myself, but someone else may have a solution. Here's a temporary one: If you're using KDE, you can use Opera; if you're using GNOME, you can use Epiphany (sudo apt-get install epiphany-browser epiphany-extensions) which behaves much like Firefox and has many of its extensions (including adblock/filterset.g and Greasemonkey).

This solution works thanks a lot, however, I want the familliarity of firefox if I can, so does anyone know how to fix it?

---

### Post by squidward_tentacels on 2006-12-02
Heres a couple of tweaks that can really speed up FireFox;

Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:
network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests
Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading. - Alter the entries as follows:
Set "network.http.pipelining" to "true"
Set "network.http.proxy.pipelining" to "true"
Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once.

- Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives.

Yes, enabling HTTP pipelining can dramatically improve networking performance. The downside, and the reason it's not enabled by default, is that it can prevent Web pages from displaying correctly. If you've enabled this, and you find pages that aren't displaying correctly, please don't blame Firefox or the Web developer. It's probably the fact that you enabled an "unsupported" feature which is incompatible with some Web servers and proxy servers.

The second change, setting the initial paint delay at zero, may get you some content on the screen faster, but it's worth noting that it will dramatically slow down the time it takes the entire page to display. Here's what's going on. Gecko, Firefox's rendering engine, is trying to optimize between the cost of waiting for a bit more data versus doing more painting and reflows as new data comes in. Waiting a bit longer before it starts painting the page gives Gecko a chance to receive more content before chewing up CPU cycles to render and reflow the document. If you drop this value down to zero or near zero, that means you'll see the page start displaying a bit earlier, but not having received much data in that short interval, you'll have a lot more paint and reflow cycles to complete rendering of the page.

This one probably comes down to a combination of bandwidth, CPU speed, and personal preference. If it works for you, and you don't mind the side-effects, then great. Just note that what works for one person/system, may not work for another.

---

### Post by Jussi01 on 2006-12-03
Wow!! the speed increase is amazing!!!!! thanks a lot!!! Huge kudo's to you!!

---

### Post by ferd on 2006-12-14
I have done all the tweaks. The only thing that helped me was to uninstall Firefox 2 and go back to firefox 1.5.08. Something is wrong with FF2 that no one at Mozilla will admit to or so it seems from the Firefox forums.

---

### Post by civic_si on 2006-12-14
I had that same issue when pointing my Ubuntu box to a Windoze  DNS server. I changed my DNS to another server and the lag went away. All I can think of is that Linux is too fast for Windoze DNS servers.

---

