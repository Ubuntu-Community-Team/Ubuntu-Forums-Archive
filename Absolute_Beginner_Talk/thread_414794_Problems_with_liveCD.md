---
title: "Problems with liveCD"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by rapolas on 2007-04-20
Hi,
I just downloaded feisty, checked the checksum, baked it, and tried to boot.. but no luck, so the problem is that I can't boot into live session. Everything boots fine until the X. When X tries to start it shows me this message:

Bactrace:
0: X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: X(InitOutput+0x9aa) [0x80a5b9a]
3: X(main+0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d44ebc]
5: X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11. Server aborting

Aborted (core dumped)

Anybody knows how to boot into liveCD session? I have ATI Mobility Radeon X1400 video card.

---

### Post by Obor on 2007-04-20
Have you tried booting into the safe graphics mode? (one of the options at the beginning)

---

### Post by rapolas on 2007-04-20
Yeap, I tried, the same thing...

---

### Post by starcraft.man on 2007-04-20
Just a suggestion but perhaps try to burn at your cd drives lowest possible speed... could be your CD has errors >.<. Another thing to think of, are you using the Regular gui desktop install? Maybe you should give Alternate CD Text [here.]("https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive")

---

### Post by rapolas on 2007-04-20
I'm sure, the CD is fine, I checked on the other computer, and it started flawlessly. I think it has something to do with my graphics card and xorg server. 
Now I'm afraid to use alternate cd, cause it doesn't have live session, and what if it's not going to work after install.. Actually it is working, but I not familiar with command line:)

---

### Post by Jhongy on 2007-04-20
Doubt it. These problems are almost always due to CD errors. Maybe the other system is pulling different files from the CD. 

I've always had similar problems with LiveCDs... just burn them slooooooowly and carefully.

---

### Post by rapolas on 2007-04-20
Ok, I will try to burn another cd, just for now I run out of cd's;) so I will try to do that later;)

---

### Post by rapolas on 2007-04-20
I didn't try to bake another cd, but I'm still thinking that it's something wrong with xorg, my video card and vesa drivers, cause, I tried these actions on my working machine. I executed command dpkg-reconfigure -phigh xserver-xorg, I chosen vesa driver and I got the same results, as I am trying to boot into liveCD. So I don't think thats a cd errors..

---

### Post by rapolas on 2007-04-20
Sorry for disturbing and thanks for advice, but it seems to be a bug, and it's already announced [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

---

