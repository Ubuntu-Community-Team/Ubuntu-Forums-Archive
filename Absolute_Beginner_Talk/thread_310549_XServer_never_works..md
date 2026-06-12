---
title: "XServer never works."
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by blake1 on 2006-12-01
Hi,
I've installed linux before on my older machine, but in April I got a new one, and I've just partitioned my disc (using GParted) to install Ubuntu.

Whenever I load the cd, or any other linux cd, it cannot load the XServer, and I get no GUI, so I cant install Ubuntu. ](*,) 

I have tried with many other distros and all of the them the same problem, apart from GParted, where it asked me what my setup was and it worked perfectly.

What is wrong? Thanks!

BTW, my specs are:
2.8Ghz Pentium D, 1024MB RAM, 160GB harddrive, Radeon X300 SE 128MB HyperMemory, and my resolution is 1280x1024. Hope that helps.

---

### Post by r4ik on 2006-12-01
Try,

sudo dpkg-reconfigure xserver-xorg

from the command-line go for the defaults and when finished
you could follow this guide,

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Good luck !

---

### Post by dca on 2006-12-01
Something to do w/ the graphics card installed.  You can try the alternate CD install...???  It's kind of like the installer used on 5.04 & 5.10 prior to the graphic installer on 6.06LTS...

---

### Post by BLTicklemonster on 2006-12-01
I guess I'd be offbase asking if you mean that, on other machines, you'd put a cd in and when you booted, you would see the install stuff from the cd, but that on this new one, you don't? If so, then I'd be tempted to comment on the need to go into your bios and set your your computer to boot from the cd. 

But I'm usually off base, so I'll just ask: have you gotten it working yet?

---

### Post by blake1 on 2006-12-02
> **BLTicklemonster said:**
> I guess I'd be offbase asking if you mean that, on other machines, you'd put a cd in and when you booted, you would see the install stuff from the cd, but that on this new one, you don't? If so, then I'd be tempted to comment on the need to go into your bios and set your your computer to boot from the cd. 

But I'm usually off base, so I'll just ask: have you gotten it working yet?
No, not yet, I cant seem to find the text based installer!

---

### Post by r4ik on 2006-12-02
Please read,

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Good luck !

---

