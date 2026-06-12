---
title: "Recovering from nvidia driver disaster"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by lalji on 2006-09-27
I followed instructions in the online guide to install nvidia drivers. I was told to restart after enabling the driver, so I did, but then X-server wouldn't start. Now I'm shut out of the graphical interface and left with only the command line off a restart!

This problem is discussed on the forums, and I believe I need to edit the X11.conf file to replace "nvidia" with "nv" so as to revert to the original setup. Unfortunately, I can't use sudo gedit because gedit won't display - no graphics .... and I don't know what other way there is to edit the file.

Any suggestions?

(I am trying to learn the command line, but I'm quite new at this still)

---

### Post by meng on 2006-09-27
Well there's
sudo vi /etc/X11/xorg.conf
but vi is not the most intuitive editor (even though I happen to like it!)

Why not try
sudo dpkg-reconfigure xserver-xorg
and choose nv as the graphics driver (default options should work for all other options)

---

### Post by lalji on 2006-09-28
And there was much rejoicing.

Some feedback:
dkpg-reconfigure worked, but it requires you to reconfigure all sorts of things, keyboard, monitor etc. I got something wrong the first time and x-server failed on a reboot.

VI is really not intuitive - at all. I was reduced to systematically hitting every key on the keyboard just to get something to happen, and ended up powering my laptop off just to get out of the editor. 

At any rate, I tried a few different settings for dpkg-reconfigure and got ubuntu to run properly. Joy.

Thank you for your help.

---

### Post by Josh1 on 2006-09-28
```

sudo dpkg-reconfigure -phigh xserver-xorg
startx

```
Try that.

---

### Post by meng on 2006-09-28
> **lalji said:**
> And there was much rejoicing.

Some feedback:
dkpg-reconfigure worked, but it requires you to reconfigure all sorts of things, keyboard, monitor etc. I got something wrong the first time and x-server failed on a reboot.

VI is really not intuitive - at all. I was reduced to systematically hitting every key on the keyboard just to get something to happen, and ended up powering my laptop off just to get out of the editor. 

At any rate, I tried a few different settings for dpkg-reconfigure and got ubuntu to run properly. Joy.

Thank you for your help.
I did warn you about vi!

---

### Post by bodhi.zazen on 2006-09-28
> sudo dpkg-reconfigure -phigh xserver-xorg
Yes this is what we should be advising.

> I did warn you about vi!
Try nano. It is easier then vi for noobs.

For noobs: Learn vi before you need it. You never know and a little vi skill can be very helpful. sudo vi may even replace sudo gedit if you are not careful... :)

8-)

---

