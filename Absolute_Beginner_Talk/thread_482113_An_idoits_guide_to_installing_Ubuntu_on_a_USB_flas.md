---
title: "An idoits guide to installing Ubuntu on a USB flash drive"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by roystondh on 2007-06-23
Hi

I've been using the Ubuntu 7.04 64 bit edition in live CD mode and absolutly LOVE IT as an OS ;) , It's nice to see a user friendly flavour of linix

Know comes the difficult part, I've got a dual boot HDD with Windows XP and XP 64 bit editions working fine. I've purchased a 4GB USB flash drive and have a motherboard that supports USB boot devices.

I used to work in IT, but quit to join the world of aviation (sorry far more fun!), so regard me as an educated end user rather than a techie, however the instuctions outlined here

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

are simply beyond me as an average user (and is the kind of linix talk that's put me off in the past), for example it mentions the HP format utility but does not specify if I need to format the USB key as a floppy or as if it was a hard drive. Also I've downloaded Partition logic partitioning tool created a ISO image, made a boot CD and it only offers HDD partitioning :(

I've tied install of the Live CD, (with the BIOS set to hide the HDD), but it sees the USB stick but does not allow me to get past the partitioning stage!

Does anybody know of a real idiots guide to getting Ubuntu onto a USB stick?

Thanks in advance

Royston H

---

### Post by bodhi.zazen on 2007-06-23
Well, :

1. 4 Gb is too small to "install" ubuntu onto (ie install in the traditional method ie install from the live CD).

2. The how-to you are following is how to boot ubuntu from a USB as if it were a live CD. Subtle difference.

[list][*]Format the flash drive as it were a had drive.

[*]Does not look too bad from there. I see you are going the Widows approach. The Linux approach would be a snap (I wonder if it could be done booting from the live CD ?? )

[*]I see there is a problem with feisty and saving your changes. 

[*]You can check this out, with qemu you can run within windows without re-booting (it will be slow and kqemu (accelerator) does not do all that much to improve speed and might break windows so skip that).

[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)

Go with a lighter version of Linux if you go with qemu (Puppy linux)


[*]Post if you get stuck again :) [/list]

---

### Post by C.S.Cameron on 2007-06-23
roystondh:
I tried that guide and most the others as well.
Finally I plugged in my 4G USB stick, unplugged the hard drives and in bios set the USB  as my second boot device after the CD.
I turned on the computer. It booted the Live CD. I hit install. 45 minutes later it was done.
I did an update, set up my e-mail account, Skype etc.
4G is plenty to run Ubuntu on if you don't go too wild on the downloads.
After installing Wine, Autocad and Rhino 3D I am getting a bit low on space.
Tried installing Autocad and Rhino on a second USB instead, it worked but was not so fast.
Eventually bought an 8G stick. I recommend a USB with about 30mbs transfer.
Cork

---

### Post by roystondh on 2007-06-23
> **bodhi.zazen said:**
> 
[*]You can check this out, with qemu you can run within windows without re-booting (it will be slow and kqemu (accelerator) does not do all that much to improve speed and might break windows so skip that).

[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)

Go with a lighter version of Linux if you go with qemu (Puppy linux)

[*]Post if you get stuck again :) [/list]

Sorry, I've just spent 45 mins downloading / extracting files to the Letter and when I run the batch file from within Windows I just get an "installation failed" error, guess I must be doing something wrong :confused:(will double check). However the end result is not what I want, I want to be able to boot the machine directly into Ubuntu from the USB drive, rather than from within another OS

If 4GB is not big enough for a regular install as you suggest, then I will carry on using the Live CD for the moment and get another HDD to install Ubuntu onto in the near future - Thanks

---

### Post by bodhi.zazen on 2007-06-23
> **roystondh said:**
> Sorry, I've just spent 45 mins downloading / extracting files to the Letter and when I run the batch file from within Windows I just get an "installation failed" error, guess I must be doing something wrong :confused:(will double check). However the end result is not what I want, I want to be able to boot the machine directly into Ubuntu from the USB drive, rather than from within another OS

If 4GB is not big enough for a regular install as you suggest, then I will carry on using the Live CD for the moment and get another HDD to install Ubuntu onto in the near future - Thanks

As pointed out, you *may* be able to squeeze into 4 Gb. You can install into just under 3.5 Gb for / and 0.5 Gb for swap ....

 Try mounting the live CD and following the linux directions rather then the windows directions.

A second HD is not a bad idea. They are not too expensive ;)

---

### Post by roystondh on 2007-06-23
> **C.S.Cameron said:**
> roystondh:
I tried that guide and most the others as well.
Finally I plugged in my 4G USB stick, unplugged the hard drives and in bios set the USB  as my second boot device after the CD.
I turned on the computer. It booted the Live CD. I hit install. 45 minutes later it was done.
Cork

Cork
Thanks I've just done exactly as suggested, physically pulled the HDD cable, set the  BIOS to boot 1st from CD then from USB, manually set the partitions on stage 4 of the install from live CD, and 30 mins later the job was done. :cool: I am writing to you as we speak from my flash drive boot into Ubuntu.

---

### Post by C.S.Cameron on 2007-06-23
roystondh:
30 minutes is good, your dongle must be faster than mine.
Let me know how much space you have left after using Update Manager?
Enjoy
Cork

---

### Post by mistergq on 2007-06-23
I had a 2004 Gateway Laptop whose hard driver controller failed in the fall 2006 (out of warranty).  I purchased a new laptop but kept the old one. 

Earlier this spring, I picked up a 2 gig flash drive and put a live cd on it so that my wife could use the laptop.  but I was frustrated that I really couldn't modify the settings.

so I picked up a 4 gig flash drive and installed it.  It took a lot longer than 30 minutes, and there were times it looked like the install was stuck, but finally, it was on the drive.  

I can't wait to get an 8 or 10 gig flash drive because at that point, you could download a lot more.

---

### Post by bodhi.zazen on 2007-06-23
> **roystondh said:**
> Cork
Thanks I've just done exactly as suggested, physically pulled the HDD cable, set the  BIOS to boot 1st from CD then from USB, manually set the partitions on stage 4 of the install from live CD, and 30 mins later the job was done. :cool: I am writing to you as we speak from my flash drive boot into Ubuntu.

Awesome :)

Welcome to Ubuntu

---

### Post by roystondh on 2007-06-23
> **C.S.Cameron said:**
> roystondh:
30 minutes is good, your dongle must be faster than mine.
Let me know how much space you have left after using Update Manager?
Enjoy
Cork

Might be a bit over 30 mins, enjoying a glass or two of wine at the moment:-P

After updates according to the system monitor I have used 2.3GB of the 3.5GB I allocated

---

### Post by C.S.Cameron on 2007-06-23
Now comes the fun part, Video drivers.
The first thing I learned after my second format and install was to back up my xorg.conf.
My first install seemed to work on anything that would boot USB.
Then I got greedy, The desk top was not perfect on the living room box using a 50" plasma and Nvidia 7800, My office computer using Nvidia 8800GTS only got one monitor at low res. My laptop with an ATI X700 and 1680 x 1060 pixels was also low res.
Unleashing Restricted drivers on the LR PC made things look good there.
But could not get to the mocha colored screen on the other computers.
Finally got duel monitors working in my office desktop using Envy.
Now the upstairs computer boots to the left monitor side that has no tool bars.
The ATI won't go near X.
I think running Ubuntu off Flash drives is the future, (understand Toishiba thinks the same about solid state)
I'm just wondering if there is a way to multi boot depending on what video card is in the machine.
The live CD seems to do this.
Cork

---

### Post by roystondh on 2007-06-23
> **C.S.Cameron said:**
> Now comes the fun part, Video drivers.

The ATI won't go near X.
I think running Ubuntu off Flash drives is the future, (understand Toishiba thinks the same about solid state)
I'm just wondering if there is a way to multi boot depending on what video card is in the machine.
The live CD seems to do this.
Cork

I am running an ATI Radeon X1650, and things are fine on a single TFT screen at 1280 x 1024, guess the fun part will be when I plumb in a second TFT

If £25 gets me 4GB flash that's £6.25 per GB, and a 160GB HD can be bought for £42 then that's £3.80 per GB then we are heading towards the economic tipping point, roll on solid state

---

### Post by roystondh on 2007-06-23
> **bodhi.zazen said:**
> Awesome :)

Welcome to Ubuntu

The support seems 1st class, looking forward to exploring the world of ubuntu - Thanks

---

### Post by C.S.Cameron on 2007-06-23
How long has it been since Flash drives cost that much per MB? A couple years?
And that was USB 1.
Cork

---

