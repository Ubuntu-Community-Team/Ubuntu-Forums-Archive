---
title: "Server X Problem with LiveCD boot"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by ChvyKc on 2006-12-06
I'm brand new to Ubuntu and Linux all together so please spell things out for me.  

I am trying to boot 6.10 from the CD on one of my computers and it is giving me a blue screen that says there is a problem with server X and that I need to configure it and reboot.

I found a couple of command lines that allow you to configure server x but I am not for sure how to use them.  Like I said, I am completely new to this.  If you guys could help me out that would be great.

I was able to boot 6.10 and 6.06 on my other computer this morning but it has a completely different video card, processor, etc so I don't know if that is causing the problem or not.  I am going to try to boot 6.06 on the computer that is giving me problems tonight.

---

### Post by taurus on 2006-12-06
At the command line, type

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by ChvyKc on 2006-12-07
> **taurus said:**
> At the command line, type

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

I believe that I just wasn't able to get to the command line because the computer would lock up with 6.10 but I did try the code in 6.06 that you recommended and it didn't work at all.  It actually scewed the way that the screen was displayed.

I did try this code:

sudo dpkg-reconfigure xserver-xorg

This did let me configure the x server but it didn't help at all.  I let the software detect the video card, keyboard, mouse and monitor and it detected everything fine but when I rebooted it did the same thing.

Any other ideas?  I'm not in a hurry to get this up and running but I would like to be able to do it sometime soon.

---

