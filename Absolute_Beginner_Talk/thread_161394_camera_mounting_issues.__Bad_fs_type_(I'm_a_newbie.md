---
title: "camera mounting issues.  Bad fs type (I'm a newbie)"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by seedman on 2006-04-16
I'm a newbie who cannot seem to mount his camera.  
It's connected via usb to my laptop.  
 xD- picture card
Olympus stylus 600 (Overpriced gadgetry. I liked my sony better)
I USED to be able to mount it.
I don't know what happened.  
Also, if you know (but I'm not hopefull) there is some garbage on the lower part of the screen. This is a second hand laptop (satellite 4030 CDS) with no manufacturers support.  I think I'm hooped there. (damn! Another excuse to upgrade to a better machine!)
-M
P.S. screenshot attached (I hope)

---

### Post by Sutekh on 2006-04-17
I like Canon's best, but lets work on your problem :)

If you plug in the camera, does it try to mount automatically?  How do you try to mount it otherwise?  If I had to hazard a guess I'd say that you were using the Disk Mounter applet in your panel.

This causes me problems with my digital audio player, resulting in a similar error.

So I mount the device from the command line (I don't know how to configure pmount - the applet uses pmount)

So plug in the camera and use this command```
sudo fdisk -l
```Hopefully it will be recognised and we can see the location of it (/dev/sdc possibly).  

You could also unplug it, then enter this command
```
tail -f /var/log/messages
```then plug in the camera and take note of the messages that appear.  The device location may appear here too.


The garbage on your screenshot looks like video driver issues.  I get these until the drivers for my NVIDIA card are installed.  I wonder what your Satellite Laptop has in terms of video card?  I'll have a look on Toshiba's site.

---

### Post by seedman on 2006-04-17
AHHHhhhh, These are the tools that allow me freedom!
Camera is now mounted!
From sdb1
you were right that I was using the disk mounter applet. command line is the way to go but learning it is difficult..
Thankyou forums ubuntu and most importantly you for helping.
ciao!
-M

---

### Post by Sutekh on 2006-04-18
[QUOTE=seedman]AHHHhhhh, These are the tools that allow me freedom!
Camera is now mounted!
From sdb1
you were right that I was using the disk mounter applet. command line is the way to go but learning it is difficult..
Thankyou forums ubuntu and most importantly you for helping.
ciao!
-M[/QUOTE]
Glad you got it working!

I really appreciate that disc mounter applet, it works great for all my hard disc partitions, but I can't seem to configure it so that it plays nice with my digital audio player.  So command line it is; its not so bad once you become familiar with it.

If you find that the location of your camera moves around (/dev/sdb1 to /dev/sdc1, etc) you may consider looking into [udev](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html).  I am planning on doing this, so I can create a mounting/unmounting script and creating a launcher/button for my palyer.  It would make life much easier.

---

### Post by patanjali on 2006-04-18
Sorry to butt into this thread, but I cannot see my camera either (Canon Powershot A200).

I tried the "tail" command (I could not see the camera in "fdisk"),and got this:

Apr 18 17:09:24 localhost kernel: [4296839.202000] usb 3-1: new full speed USB device using uhci_hcd and address 4

Now what do I do?

I really appreciate the help everyone gives on this forum.

Thanks

Patanjali  :-k

---

### Post by seedman on 2006-04-29
I'm not sure if this'll help but:
while trying the fdisk I didn't type sudo first and that didn't work.
I'm not very familiar with how the forums work, but I don't mind at all that you join! however I'm unsure if replying in this thread is the best place to get results.
If my problems can help guide the way for others then let me **** up!
I'm only back here for referance because I'm trying to mount my Ipod!
Best of luck

---

