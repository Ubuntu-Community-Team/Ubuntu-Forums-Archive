---
title: "weird connection with wireless"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by creperum on 2007-02-14
I have a weird problem with my wireless connection.

I was visiting a friend a couple of times, and conencted to the Internet via her neighbour's wireless Internet, no problem.  When connected, I can use ssh just fine, but web browsers (I tried Firefox and Epiphany both) worked oddly: only some web pages would load, while others would take a long time and then come up with a "this page is unavailable" error message.  Even if a page would load, it would take a long, long time.

Does anyone have any ideas what might be causing this problem?

I tried to determine what sorts of pages would or wouldn't load, and I couldn't come up with decent criteria.  Popular webpages like yahoo and google didn't ever load; a couple of pages from the same city (the university and a local bookstore) did load.  I note also that other people who live in the house did not have this problem (I'm pretty sure they were running Windows).

I realize this note is somewhat lacking in detail, but I couldn't post to the forum when I was having the problem, since the Ubuntu Forums page was taking tens of minutes to load.  I'm happy to provide any technical info that would be helpful.  I'm going back to visit in a few days, and I'd love to have some ideas of things to try if I have the same problem again.

---

### Post by ukripper on 2007-02-15
> **creperum said:**
> I have a weird problem with my wireless connection.

I was visiting a friend a couple of times, and conencted to the Internet via her neighbour's wireless Internet, no problem.  When connected, I can use ssh just fine, but web browsers (I tried Firefox and Epiphany both) worked oddly: only some web pages would load, while others would take a long time and then come up with a "this page is unavailable" error message.  Even if a page would load, it would take a long, long time.

Does anyone have any ideas what might be causing this problem?

I tried to determine what sorts of pages would or wouldn't load, and I couldn't come up with decent criteria.  Popular webpages like yahoo and google didn't ever load; a couple of pages from the same city (the university and a local bookstore) did load.  I note also that other people who live in the house did not have this problem (I'm pretty sure they were running Windows).

I realize this note is somewhat lacking in detail, but I couldn't post to the forum when I was having the problem, since the Ubuntu Forums page was taking tens of minutes to load.  I'm happy to provide any technical info that would be helpful.  I'm going back to visit in a few days, and I'd love to have some ideas of things to try if I have the same problem again.



Find out whether connection is using automatic DHCP or static one. Try it with auto DHCP I reckon settings are using static ip address which is muking up.

---

### Post by creperum on 2007-02-19
Thanks for the reply--sorry to take so long to post again.

I'm at the friends' house now, and I'm still having the same problem: some pages load fine (like to local college's page, and (fortunately) this one), while some take forever or never load (like Google).  Using ssh to connect to my work server works fine.

ukripper writes:
> Find out whether connection is using automatic DHCP or static one. Try it with auto DHCP I reckon settings are using static ip address which is muking up.

I think it's automatic.  How do I tell?  It's set to auto in my /etc/network/interfaces file.  Is there another way to tell?  

If anyone has any other ideas what might be going on, I'd love to hear them..... 

thanks!

---

