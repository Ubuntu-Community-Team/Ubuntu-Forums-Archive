---
title: "Swapped ISP - internet problem"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-02-14
Access in XP is perfectly fine.

In ubuntu, GAIM will not connect and websites are taking 5+ mins to open if at all.

Do I need to change something?

---

### Post by m.musashi on 2006-02-14
I had the exact same problem and started [this](http://ubuntuforums.org/showthread.php?t=126764) thread. You may be able to find something in there to help you fix your problem. For my wired connection I found that option 3 (discussed in [this](http://www.ubuntuforums.org/showthread.php?t=78337&page=2) thread) seemed to be the one that fixed it. Although I did several other changes before that so it may have be a cumulative effect.

I would suggest changing one thing at a time and try to isolate what works. I didn't do a very good job there. Of course, while this did fixed my wired connection I have no wireless now. I'm in the process of working on that.

---

### Post by _simon_ on 2006-02-14
after getting totally stumped i decided to reinstall.

I now have internet access BUT GAIM still will not connect and i can only view a website via it's IP as the domain name will not resolve :(

---

### Post by _simon_ on 2006-02-14
scrap the above.

It's now working. I followed option 3 but it never saved the nameservers - tried again and it has :)

thanks loads

---

### Post by m.musashi on 2006-02-14
I don't blame you. I've considered reinstalling too, but for some strange reason I'm enjoying the troubleshooting. Of course, I don't NEED my laptop to work with Ubuntu. I'm just learning.

Check your /etc/resolv.conf file. The IPs listed should correspond to the DNS IPs from your ISP. I had to call my ISP and get the right ones. I'm not sure about the GAIM problems as I haven't used it much and don't really know how it works. However, if you are having DNS problems that could also be affecting GAIM.

EDIT: nevermind. Seems you solved it while I was writing my response. Glad it's working for you.

---

### Post by mips on 2006-02-14
Did you disable IPv6 ?

Have a look at the thread/link referenced above.

---

