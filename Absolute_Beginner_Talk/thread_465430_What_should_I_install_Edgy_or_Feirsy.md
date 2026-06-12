---
title: "What should I install Edgy or Feirsy?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Balistic on 2007-06-05
I have a dell e1705, I've made a dual boot with vista and feisty, just to experiment a little bit.  Had many many problems configuring feisty, and eventually ended up messing it all up, vista is also not my cup of tea for now.  So I'm going to format my HDD and start over with win-xp pro and Ubuntu.  Now I'm wondering if this time I should go for feisty again, or if it'll be easier to configure beryl and wifi easier on Edgy.  Any thoughts?

---

### Post by Crafty Kisses on 2007-06-05
> **Balistic said:**
> I have a dell e1705, I've made a dual boot with vista and feisty, just to experiment a little bit.  Had many many problems configuring feisty, and eventually ended up messing it all up, vista is also not my cup of tea for now.  So I'm going to format my HDD and start over with win-xp pro and Ubuntu.  Now I'm wondering if this time I should go for feisty again, or if it'll be easier to configure beryl and wifi easier on Edgy.  Any thoughts?

Go for Feisty.

---

### Post by tdrusk on 2007-06-05
> **Balistic said:**
> I have a dell e1705, I've made a dual boot with vista and feisty, just to experiment a little bit.  Had many many problems configuring feisty, and eventually ended up messing it all up, vista is also not my cup of tea for now.  So I'm going to format my HDD and start over with win-xp pro and Ubuntu.  Now I'm wondering if this time I should go for feisty again, or if it'll be easier to configure beryl and wifi easier on Edgy.  Any thoughts?
I've been using Feisty and it's running great. I'd recommend it. 

What is your wireless card? If you don't know go to the terminal and run
```
lspci
```

---

### Post by Balistic on 2007-06-05
My wireless is intel 4965 aka intel wireless N.  I was able after a lot of trouble to get it to recognize the wireless networks, but never managed to actually connect.
as for video card, I have nVidia 7900GS, and though I was able to install beryl, it was pretty much messed up, and didn't function very well.  This is why I thought maybe Edgy will be a little easier...

---

### Post by tdrusk on 2007-06-05
According to [this post]("http://ubuntuforums.org/showpost.php?p=2735506&postcount=20") you need ndiswrapper 1.45rc (the new 1.46 is more stable and will *probably* work) and the latest XP driver.

Sorry I can't help much.

[This guide]("http://www.mneylon.com/blog/archives/2007/03/18/configuring-nvidia-geforce-7900-gs-on-ubuntu-edgy-using-envy/") should help you with your video.

EDIT: to fix your video [this guide]("http://www.psychocats.net/ubuntu/nvidia") would be more useful.

Best of luck!

---

### Post by jvc26 on 2007-06-05
Feisty has better wireless support, and is generally an improvement on edgy. I'd recommend going with Feisty.
Il

---

### Post by Praill on 2007-06-05
I have the exact same laptop, have tried both, and I stuck with edgy.
For me, since I have an ati card, feisty was a pain since the vesa drivers and the new kernel dont play nice with my card. Also my particular webcam wouldnt work with the new kernel and there were a few media formats I culdnt get to play with totem.
Everything works great on the e1505 with edgy right out of the box. And any open source projects are more likely to work with an older kernel than a brand new one.
For ME, feisty offers nothing new but lesser functionality.. but for others its apprently better with printers and scanners and things.

---

### Post by mikledet on 2007-06-06
I think Praill is right.  For now Feisty is like a beta software, if it works for you and all is fine then you're lucky and can enjoy the latest.  But if stuff doesn't work for you easy enough or at all, maybe trying Edgy will be better.

---

