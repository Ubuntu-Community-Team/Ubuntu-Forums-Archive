---
title: "laptop with external  monitor problem"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2008-03-02
ok heres the story, I own an Inspiron b120 dell laptop.  These cheap dell models are unanimously known to have the hinges on their screen break after a while and crazy things happen to it, so it happened and my screen broke. 

 I was forced to use an external CRT monitor and I got some bad results, it would only stay within an 800 by 600 resolution and every time I booted ubuntu (I have a dual boot), It gave me an error message that my graphics would remain in low graphics mode and something about not being able to detect graphics hardware.  

I use Gutsy and my specs are 1.4 ghz celeron M, 1gb ram, and a intel GMA 950 with 64 mb memory.  I did go through the screens and graphics in the system settings, told it my monitor model and everything, made the CRT default but it just wouldn't work. 

Any help would be appreciated to reach a better resolution.  Thanks.

---

### Post by djbsteart1 on 2008-03-03
Your lucky, I have the sme issue but with a nvidia card. The monitor does not work ith the driver enable, I get around 600*480 res. you could try to reconfigure the x server using 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

But make a backup first using


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

