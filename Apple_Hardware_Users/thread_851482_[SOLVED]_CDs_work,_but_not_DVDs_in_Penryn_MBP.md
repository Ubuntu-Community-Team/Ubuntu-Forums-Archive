---
title: "[SOLVED] CDs work, but not DVDs in Penryn MBP"
date: 2008-07-06
forum: Apple Hardware Users
---

### Post by MaddMatt on 2008-07-06
Hi all, 

I've been trying to watch some movies on my MBP here, and the DVD drive doesn't seem to want to cooperate with Totem / ACIDburn / mPlayer etc. The only one the kind of worked was gxine, but it only plays the title track, and then stops. Errors range from: Totem: "An error occurred, could not read from resource" to "Cannot read disc, encrypted", "Error reading NAV packet", etc. I've tried it on 4 different DVDs tonight, and 1 other one 2 weeks ago. Browsing the discs is no problem in Nautilus. Nothing looks out of the ordinary. ACIDburn crashes to the background without outputting any errors to the terminal. (which is super weird because my CPU load stays at 45% but System Monitor shows only itself using CPU. That's very odd.)

I ran k3b, and nothing seems out of the ordinary. k3b detects it just fine, and reports that it can read and write all of the formats. So what gives? The messages are useless, so I really can't come up with anything. 

Ideas?
Anyone else having this problem?

Cheers, 
-M

---

### Post by DonnieP on 2008-07-06
Are you saying this used to work and now doesn't?

---

### Post by MaddMatt on 2008-07-07
I cannot verify that it has or has not worked previously because I had not tried to watch a DVD until very recently. The Ubuntu / MacbookPro setup is new for me, but I certainly never had problems watching DVDs on my tower. Of course I had Automatix before too, but I made sure that I had all of the codecs and encryption bits last night as well and no progress. 
But, Since I've gotten this setup, it has not worked. 

Thanks, 
-M

---

### Post by nikgare on 2008-07-07
You need to install **libdvdcss2** to be able to view encrypted movie dvds, ie most dvds.
You mey need to enable **multiverse** in the Sytem->Adminstration->Software Sources menu.

---

### Post by MaddMatt on 2008-07-07
Thanks! I don't remember ever having to do this special work on my tower, but I actually used some debian repositories to get the correct codecs. Here's the link for reference.

[http://www.pendrivelinux.com/2007/10/09/how-to-make-totem-media-player-play-encrypted-dvds/](http://www.pendrivelinux.com/2007/10/09/how-to-make-totem-media-player-play-encrypted-dvds/)

However the colors are really screwy on the DVD... But that's rather a minor problem. Just need to calibrate.

---

### Post by nikgare on 2008-07-07
I had that once, but it webt away after awile - I've no idea why.
While I had this problem, I adjusted the **hue** setting in totem.

---

