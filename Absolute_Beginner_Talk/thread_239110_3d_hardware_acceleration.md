---
title: "3d hardware acceleration"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-08-18
Hi,

How do I go about enabling 3d hardware acceleration, I have onboard graphics card (128mb SiS chipset)

Thanks in advance

---

### Post by zxee on 2006-08-18
I think-someone please correct me if I'm wrong-that you are stuck with the open source driver for that card. There isn't any linux driver from the maker.
Do you have an AGP slot? Because if you do you could get a nvidia or ati gpu that does have accleration support.

---

### Post by jd65pl on 2006-08-18
its a laptop so not much option for expansion in terms of graphics, but if there is a posibility a graphics card will work on my machine ill give it a go

---

### Post by zxee on 2006-08-18
I didn't realize it was a laptop.
There is some more info here: [http://www.die.net/doc/linux/man/man4/sis.4.html](http://www.die.net/doc/linux/man/man4/sis.4.html)
Have a look at /etc/X11/xorg.conf and note which driver is called out for device.

---

### Post by boomstik on 2006-08-18
I also can't figure out the hardware acceleration, and would very much appreciate some help.... 
I'm running Dapper Drake on a Dell Inspiron 5000e with a 16Mb ATI Rage Mobility graphics adapter. Right now I can clearly see that the interface is not hardware accelerated. If I launch glxgears, they barely move, and glxinfo reports Direct=NO.
My "ultimate" :) goal right now is getting xgl and compiz running.

So, before I jump into following the HowTo's, I'm trying to understand the following (danger, totally lame n00b questions ahead):

1) Is "direct rendering" the same thing as "hardware acceleration"?
2) Do I need to figure out DRI before starting with xgl/compiz? Or will installing xgl somehow also enable harware acceleration?
3) xgl, fglrx, aiglx, mesa - what's the difference between all of those, and which one should I use?

I've read through the forums, but can't figure out in which order to take steps. If someone could nudge me in the right direction... that would be just awesome :)

Thanks!

---

### Post by jd65pl on 2006-08-19
```
Have a look at /etc/X11/xorg.conf and note which driver is called out for device.
```

The driver is versa

Anyone know where I might find a SiS driver for it! Thanks for the help so far I feel I have made some progress in understanding this.

---

