---
title: "64 bit gusty?"
date: 2007-09-29
forum: Apple Intel Users
---

### Post by wootwoot123 on 2007-09-29
Is there any downside in running the 64 bit version on my macbook instead of the 32 bit version other than the few things like flash plugins and such? Will my wireless work fine?

---

### Post by Infinite Recursion on 2008-03-22
Personally, I have had no problems with Gutsy x64 on my C2D.  Installing the latest madwifi drivers works just fine, and I can deal with the few problems with software compatibility (Flash works with a little tweaking, so that's fine for me).  If you're unsure, though, a good place to start would be the sticky at [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by veiho on 2008-03-24
Madwifi atheros driver doesn't support power management. I don't know how are things with ndiswrapper.

---

### Post by hackersmovie on 2008-03-24
I'm not sure if I got a funky Macbook or what but, my wireless card is not an Atheros, it's a Broadcom, so it's no wonder why all the "fixes" don't work. I've tried the madwifi and ndiswrapper, neither worked. I did get the ndiswrapper to work, for a bit, with the Dell drivers of all things! But, nothing lasting. 

Am I missing something here? A post perhaps? a Wiki? My mind? A brain?

I digress. . .

---

### Post by Mr. Pink on 2008-03-24
>  
I'm not sure if I got a funky Macbook or what but, my wireless card is not an Atheros, it's a Broadcom, so it's no wonder why all the "fixes" don't work. I've tried the madwifi and ndiswrapper, neither worked. I did get the ndiswrapper to work, for a bit, with the Dell drivers of all things! But, nothing lasting.

Am I missing something here? A post perhaps? a Wiki? My mind? A brain?




I believe the newer Macbooks (Santa Rosa) all have Broadcom wireless cards.  I followed the wireless steps here:

[Macbook Santa Rosa]("https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b")

And mine works perfectly.

---

### Post by hackersmovie on 2008-03-24
> **Mr. Pink said:**
> I believe the newer Macbooks (Santa Rosa) all have Broadcom wireless cards.  I followed the wireless steps here:

[Macbook Santa Rosa]("https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b")

And mine works perfectly.

Thanks! I had followed that from another site I found, save but the launch ndiswrapper at login! that's what I was missing! Hopefully it will work next time too!

---

### Post by cyberdork33 on 2008-03-24
There are both. Most Macs tend to have Broadcom. Older Macbooks and Macbook Pros have Atheros.

---

