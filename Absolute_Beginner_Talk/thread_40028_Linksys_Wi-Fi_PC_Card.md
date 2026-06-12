---
title: "Linksys Wi-Fi PC Card"
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by laurarobeson on 2005-06-07
I successfully installed Ubuntu on my Dell Inspiron this weekend and so far it looks good, except that it doesn't recognize my wi-fi connection. How do I get my wi-fi card to work again?

It's hard to take advantage of this forum when I can't use my computer to get online, I have to do it from work. So any help would be greatly appreciated, I know very little about Linux, I can follow step-by-step instructions, but I really am quite the beginner. Not new to computers though, not by any means. I'm just a graphic design person, not a code-writer.


Thank you!!

Laura

---

### Post by Gtaylor on 2005-06-07
Depending on your chipset, you may be all set. Do you happen to know what kind of card you have? My Dell came with a broadcom so I had to use ndiswrapper (do a forum search for help with this). Although some cards work by just loading a kernel module.

---

### Post by laurarobeson on 2005-06-07
I'm at work so I can't double-check, but I'm 99% sure it's a Linksys WPC54G Wireless-G Notebook Adapter. Is that what you were asking?

---

### Post by Gtaylor on 2005-06-07
Yeah. That's what I run and I had to go the route of ndiswrapper. Check out these threads:

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper)

The first one is the ideal situation. It's fairly straightforward, give it a shot and let us know if you have any problems.

---

