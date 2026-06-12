---
title: "Help Needed in Ubuntu."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by shooting_rubber on 2008-02-28
Hello,

I have successfully dual-booted Ubuntu and XP, which I am very happy with.  Although there is one problem I am having.  How do I install the driver for my wireless network card?  It shows up in the Restricted Drivers Manager, but how do I install the driver/firmware?  My network card is "Broadcom 440x 10/100 Integrated Controller.

Also when I type 

> sudo pico /etc/usplash.conf

in the terminal and I change the xres and yres, how do you save the changes you've made?

Thanks Again.

---

### Post by celticbhoy on 2008-02-28
Try this thread :-

[http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+440](http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+440)

---

### Post by The Cog on 2008-02-28
> **shooting_rubber said:**
> 
Also when I type 
sudo pico /etc/usplash.conf
in the terminal and I change the xres and yres, how do you save the changes you've made?


Hit Ctrl-X for exit and it asks if you want to save the changes. Type y for yes or n for no followed by enter.

---

### Post by shooting_rubber on 2008-02-28
Thanks for the link, but I am still having trouble connecting to the internet wirelessly.  I could install the driver from the disc, but the maximum speed from that is 11 mb/s.

Any ideas?

Thanks.

---

### Post by shooting_rubber on 2008-02-28
> **shooting_rubber said:**
> Thanks for the link, but I am still having trouble connecting to the internet wirelessly.  I could install the driver from the disc, but the maximum speed from that is 11 mb/s.

Any ideas?

Thanks.

Even when I try to install the driver from the Restricted Drivers Manager it doesn't work?  I am connected to the internet using a wired connection right now and I am writing this post from the Ubuntu OS.

Thanks.

---

### Post by celticbhoy on 2008-02-28
Its not my kind of card but a search through the forums will offer a multitiude of different posts

---

### Post by jan quark on 2008-02-28
perhaps you have to enable the software sources

go to

system > administration > software sources

and enable everything except source code and cd

then run in terminal

```
sudo apt-get update
```

and try to install one more time

---

### Post by shooting_rubber on 2008-02-28
Okay, thankyou, I'm pretty sure that worked, but when I go to Appearance, go to visual effects and then click extra, it doesn't enable and a message comes up.  I can't tell you exactly what it says because I'm on XP now.

Thanks.

---

