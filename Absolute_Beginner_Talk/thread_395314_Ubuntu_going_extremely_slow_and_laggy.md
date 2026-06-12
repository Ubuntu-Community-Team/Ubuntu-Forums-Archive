---
title: "Ubuntu going extremely slow and laggy"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Malik on 2007-03-28
Ubuntu sometimes takes forever to load a program up and i can just feel the lag and slowness. today I couldnt even type on GAIM the lag was killing me. This has been going on since I installed it. How can I fix this?

I got a p4 3ghz with 1gig ram. I use a intel video card that came with the computer.

---

### Post by thelinuxguy on 2007-03-28
> **Malik said:**
> Ubuntu sometimes takes forever to load a program up and i can just feel the lag and slowness. today I couldnt even type on GAIM the lag was killing me. This has been going on since I installed it. How can I fix this?

I got a p4 3ghz with 1gig ram. I use a intel video card that came with the computer.

After a fresh install of Edgy, I had to install the video drivers. Without the nvidia drivers for my chipset, I had similar experiences. I could literally see the frame by frame updates to my screen. But it was always and not sometimes as you have mentioned. Video drivers may be the issue. But I am not sure.

Could you post something more that can give a clue. Like some other weird behavior apart from the lag that is noticeable. Or some software you recently installed......

---

### Post by seshomaru samma on 2007-03-28
also what is the output for this command :
```
top
```

---

### Post by Malik on 2007-03-28
> **thelinuxguy said:**
> After a fresh install of Edgy, I had to install the video drivers. Without the nvidia drivers for my chipset, I had similar experiences. I could literally see the frame by frame updates to my screen. But it was always and not sometimes as you have mentioned. Video drivers may be the issue. But I am not sure.

Could you post something more that can give a clue. Like some other weird behavior apart from the lag that is noticeable. Or some software you recently installed......
its always now. I got a intel chipset. How do i update it?

---

### Post by thelinuxguy on 2007-03-28
> **Malik said:**
> its always now. I got a intel chipset. How do i update it?

It seems like **xserver-xorg-video-i810** is the driver package for Intel drivers. But a couple of sites and forums here (like the one at [http://ubuntuforums.org/showthread.php?t=386442](http://ubuntuforums.org/showthread.php?t=386442)) mention that this package is installed by default. I checked on my system and it indeed is installed even though I have an AMD system with an nVidia chipset.

See if it is installed at your end as well.
System >> Manager >> Synaptic Package Manager

You may also want to go through the page at [http://www.metlin.org/2007/02/05/installing-beryl-on-ubuntu-edgy-with-an-intel-chipset/](http://www.metlin.org/2007/02/05/installing-beryl-on-ubuntu-edgy-with-an-intel-chipset/). The part about installing the Intel drivers and fixing some problems that followed comes after the 5 Beryl screenshots.

Be aware that if the driver installation fails for some reason, you may end up locking yourself out of the GUI and with some additional trouble reconfiguring X. However, this is just a possibility and need not be necessary.

Let me know what works for you.

---

### Post by kinkdxm on 2007-03-28
hey thanks thelinuxguy.
I had a old computer with onboard video I threw ubuntu on and it didn't seem to work right.
I'll take a look at those links.
thanks

---

### Post by thelinuxguy on 2007-03-28
> **kinkdxm said:**
> I had a old computer with onboard video I threw ubuntu on and it didn't seem to work right.


A similar problem, which  remained even after trying the graphic card drivers, was solved by installing a different kernel version. Take a look at [http://ubuntuforums.org/showthread.php?t=395243](http://ubuntuforums.org/showthread.php?t=395243)

Do post the resolution to your problem when you get it.

---

### Post by kinkdxm on 2007-03-28
> **thelinuxguy said:**
> A similar problem was solved by installing a different kernel version. Take a look at [http://ubuntuforums.org/showthread.php?t=395243](http://ubuntuforums.org/showthread.php?t=395243)
is it a security risk to not use the latest kernel?

---

### Post by ceeg on 2007-03-28
Try this real quick:

```

sudo nano /etc/hosts

```

edit this file to look like this:
```

127.0.0.1         localhost           hostname
127.0.1.1         hostname

```

Restart gnome:
```

sudo /etc/init.d/gdb restart

```

If you get a blank screen trying to restart gnome, just reboot your system. This seems to help out a lot of people with laggy applications.

---

### Post by Malik on 2007-03-29
> **thelinuxguy said:**
> It seems like **xserver-xorg-video-i810** is the driver package for Intel drivers. But a couple of sites and forums here (like the one at [http://ubuntuforums.org/showthread.php?t=386442](http://ubuntuforums.org/showthread.php?t=386442)) mention that this package is installed by default. I checked on my system and it indeed is installed even though I have an AMD system with an nVidia chipset.

See if it is installed at your end as well.
System >> Manager >> Synaptic Package Manager

You may also want to go through the page at [http://www.metlin.org/2007/02/05/installing-beryl-on-ubuntu-edgy-with-an-intel-chipset/](http://www.metlin.org/2007/02/05/installing-beryl-on-ubuntu-edgy-with-an-intel-chipset/). The part about installing the Intel drivers and fixing some problems that followed comes after the 5 Beryl screenshots.

Be aware that if the driver installation fails for some reason, you may end up locking yourself out of the GUI and with some additional trouble reconfiguring X. However, this is just a possibility and need not be necessary.

Let me know what works for you.

there is no system >> Manager

---

### Post by Malik on 2007-03-29
i found it. but my video card is a Intel® 82915G/82910GL Express Chipset Family

---

### Post by thelinuxguy on 2007-03-29
> **Malik said:**
> there is no system >> Manager

My mistake. Should have been: System >> Administration >> Synaptic Package manager

---

### Post by Malik on 2007-03-29
> **thelinuxguy said:**
> My mistake. Should have been: System >> Administration >> Synaptic Package manager
yea its installed. Still slow.

---

### Post by thelinuxguy on 2007-03-29
If your drivers are installed and the system is still slow then the problem seems to be elsewhere.

Does ceeg's suggestion solve your problem?
If not, then post the output of top as suggested by seshomaru samma.
We can keep the kernel downgrade as the last option.


@kinkdxm:
This is a subjective question and really depends on what was fixed in the latest kernel. 
If it was some major security hole which was plugged, then upgrading is highly recommended.
However, under certain circumstances, like this one, downgrading to a previous version may prove useful.

And to be sure about the security implications, getting hold of a list of items that the new kernel added/modifed should be fine.
Someone more knowledgeable on this may be able to point you to such a list.

---

### Post by Malik on 2007-03-29
> **thelinuxguy said:**
> If your drivers are installed and the system is still slow then the problem seems to be elsewhere.

Does ceeg's suggestion solve your problem?
If not, then post the output of top as suggested by seshomaru samma.
We can keep the kernel downgrade as the last option.


@kinkdxm:
This is a subjective question and really depends on what was fixed in the latest kernel. 
If it was some major security hole which was plugged, then upgrading is highly recommended.
However, under certain circumstances, like this one, downgrading to a previous version may prove useful.

And to be sure about the security implications, getting hold of a list of items that the new kernel added/modifed should be fine.
Someone more knowledgeable on this may be able to point you to such a list.
i dont know how to save the changes he told me to do.

---

### Post by Malik on 2007-03-30
i found out i got the driver installed but its still running slow

here's my specs.

[http://support.gateway.com/s/PC/R/3724/3724sp25.shtml](http://support.gateway.com/s/PC/R/3724/3724sp25.shtml)

---

### Post by thelinuxguy on 2007-03-31
> **Malik said:**
> i dont know how to save the changes he told me to do.

Referring to post by ceeg at [http://ubuntuforums.org/showpost.php?p=2369300&postcount=9](http://ubuntuforums.org/showpost.php?p=2369300&postcount=9)

Terminal >> sudo nano /etc/hosts
Make the changes.
Ctrl + O followed by an {Enter} to save.
Ctrl + X to quit nano.

These commands are at the bottom of the screen when you start nano.

Let me know if this speeds up your system.

---

