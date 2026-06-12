---
title: "[SOLVED] Resizing root partition using GParted"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-07-21
I need to enlarge my root partition (ext3).  I took 5 Gigs from my home partition, and the unused space is adjacent to the root partition, but when I try to add space to it, it says that the maximum size is the current size of the root partition.  Can anyone help me?

Thanks.

---

### Post by Yes on 2007-07-21
Bump.

---

### Post by ramjet_1953 on 2007-07-21
Are you trying to do this while running Ubuntu?

You cannot re-size any partition when it is mounted.

What I suggest you do is download the GParted live CD iso and burn the iso to a CD.

You then boot from the CD and can change partitions to your heart's content.

You can get the iso from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Regards,
Roger:cool:

---

### Post by Yes on 2007-07-21
The partitions are unmounted.  I can resize, move, delete, do whatever to the home partition, but I can't make the root partition larger.  I do have unused space.

---

### Post by Yes on 2007-07-21
Bump.

---

### Post by ramjet_1953 on 2007-07-22
Just to clarify things, are you trying to do this with the GParted iso image CD, like I said, or from within a running Ubuntu session?

Regards,
Roger :cool:

---

### Post by AlexenderReez on 2007-07-22
hm..i never test gparted livecd...is it has function like norton partition magic,can resize partition without delete anything inside ?

:)

---

### Post by ramjet_1953 on 2007-07-22
Yes, the GParted live CD can do any partitioning on an unmounted HDD, and handle virtually any format.

As long as you don't try to make the partition less than the active data that is already in the partition, you will not have a problem.

It boots from its own Linux OS.

Don't forget, when you burn ANY iso burn it SLOWLY, 4 X or less.

Regards,
Roger :cool:

---

### Post by tarek on 2007-07-22
I used gparted on the live cd to resize the root partition and create a separate home partition. Worked just fine.

TK

---

### Post by bodhi.zazen on 2007-07-22
As ramjet_1953 advised, you will need to use the gparted live CD

This is because :

1. you can not re-size a partition if it is mounted (thus the need for a live CD)

2. The version of gparted on the ubuntu CD is outdated and does not have the functionality you need, they the gparted live cd.

---

### Post by Yes on 2007-07-22
Thanks for the replies.  I have made the live CD, and tried booting from the Ubuntu Live CD (As I cannot log into my Ubuntu account on the hard drive, at the moment).  Once I booted from the Ubuntu CD, I thought I would run GParted from the GParted Live CD, but I couldn't find an executable file.  Then I tried booting from the GParted Live CD, and I was given a list of about twenty options of what to boot.  I chose the first one, although I have no idea if that was the right choice.  Then, a bunch of words came on the screen, and they started to scroll past.  I was given a choice for something, I didn't know what it was, so I just chose the default.  Then I chose my language.  Some more words scrolled by, and then a bunch of red words flashed on the screen, then the screen went black and said "Input signal out of range".  I let it sit for a few minutes, but then I gave up and booted back into Windows.  Can anyone explain to me how I am supposed to run GParted from the GParted Live CD?

Thanks.

---

### Post by tarek on 2007-07-22
> **Yes said:**
> Thanks for the replies.  I have made the live CD, and tried booting from the Ubuntu Live CD (As I cannot log into my Ubuntu account on the hard drive, at the moment).  Once I booted from the Ubuntu CD, I thought I would run GParted from the GParted Live CD, but I couldn't find an executable file.  Then I tried booting from the GParted Live CD, and I was given a list of about twenty options of what to boot.  I chose the first one, although I have no idea if that was the right choice.  Then, a bunch of words came on the screen, and they started to scroll past.  I was given a choice for something, I didn't know what it was, so I just chose the default.  Then I chose my language.  Some more words scrolled by, and then a bunch of red words flashed on the screen, then the screen went black and said "Input signal out of range".  I let it sit for a few minutes, but then I gave up and booted back into Windows.  Can anyone explain to me how I am supposed to run GParted from the GParted Live CD?

Thanks.

It seems that you have the alternative cd, you can use that too but it's not as easy as the graphical one.

You should probably use the Desktop Live CD, there you'll get the same desktop as if you have Ubuntu installed. Go to System > Administration > GParted.

TK

---

### Post by Yes on 2007-07-22
Thats not the same one as the one on the Ubuntu Live CD, is it?  Where do I get the Desktop Live CD?  I got the other GParted Live CD from the GParted website, but I didn't see any other version.

Thanks.

---

### Post by tarek on 2007-07-22
> **Yes said:**
> Thats not the same one as the one on the Ubuntu Live CD, is it?  Where do I get the Desktop Live CD?  I got the other GParted Live CD from the GParted website, but I didn't see any other version.

Thanks.

Oh, I see. I've never used the one you mentioned so I can't help you there. But if you want, you could use Ubuntu's CD, you can use the same CD you installed Ubuntu from or go to [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) and download the Desktop iso.

TK

---

### Post by Yes on 2007-07-22
Ok, thanks.  The thing is, I've already tried using the GParted on the Ubuntu CD.  I unmounted all the partitions on my external hard drive (Where Ubuntu is installed), and then I took 5 Gigs from my home partition.  Then I tried adding those 5 Gigs to my root partition, but it wouldn't let me.  It said that my current amount of space was the maximum amount of space for my root partition.  Now, I know that you can enlarge your root partition, but I just can't figure out how.  Can anyone help me?

Thanks.

---

### Post by Yes on 2007-07-22
Bump.

---

### Post by Yes on 2007-07-22
Bump.

---

### Post by bodhi.zazen on 2007-07-22
Hard to tell with the information you provided. You might have to move a partition so the free space is adjacent to your root partition, just a guess though.

Also, FYI, bumping your threads frequently is considered poor etiquette.

---

### Post by Yes on 2007-07-22
Sorry about the bumping, I was afraid that no one would bother checking past the first page for topics to reply in.  It won't happen again.

In GParted, there is a picture of all the partitions, with each of them a rectangle.  First, there is the boot partition.  Then the home, then the unused space, and then the root partition.  This means that the root partition is adjacent to the free space, correct?

---

### Post by bodhi.zazen on 2007-07-22
Should work. what version of gparted are you using ? the gparted llve CD ?

---

### Post by Yes on 2007-07-22
The version that comes on the Ubunu Live CD.  If you'll read my first post on the second page, you'll see what happened when I tried usinbg the GParted Live CD.

---

### Post by bodhi.zazen on 2007-07-22
Ah, Now I see.

Well the version of gparted on the Ubuntu CD is older and will not accomplish the task (as you can see).

Reboot the gparted CD and try to work through the options, go with vesa for your video driver.

If that fails, and you boot to the command line, manually change to the vesa driver.

nano /etc/X11/xorg.conf

In the "Device" section, change to 

"Driver" "vesa'

Save and exit ...

Start X with "startx" or "startfluxbox" (without quotes).

You other option is to look for an alternate live CD with a more up to date version of gparted ( version 3.4 +)

?Knoppix

---

### Post by e6626550w on 2007-07-22
> **Yes said:**
> Thanks for the replies.  I have made the live CD, and tried booting from the Ubuntu Live CD (As I cannot log into my Ubuntu account on the hard drive, at the moment).  Once I booted from the Ubuntu CD, I thought I would run GParted from the GParted Live CD, but I couldn't find an executable file.  Then I tried booting from the GParted Live CD, and I was given a list of about twenty options of what to boot.  I chose the first one, although I have no idea if that was the right choice.  Then, a bunch of words came on the screen, and they started to scroll past.  I was given a choice for something, I didn't know what it was, so I just chose the default.  Then I chose my language.  Some more words scrolled by, and then a bunch of red words flashed on the screen, then the screen went black and said "Input signal out of range".  I let it sit for a few minutes, but then I gave up and booted back into Windows.  Can anyone explain to me how I am supposed to run GParted from the GParted Live CD?

Thanks.

Forget about it. Some computers have the same experience trying to use the 'Gparted live cd ' as you did. I got the black screen too. I checked their forum out last night and this is a problem that hasn't been resolved as of yet. 

In fact, Gparted  on both the ubuntu and xubuntu version of 7.04 didn't work for me either. Refused to resize a partition. However Gparted on an older version of ubuntu did work okay. The version before this one. I believe they called it 'edgy' or 6.10. 

eileen...

---

### Post by Yes on 2007-07-22
Right, I chose "Force VESA Drivers", and it worked!  I resized my root partition and can now log into Ubuntu!

Thank you to everyone who helped!

---

### Post by bodhi.zazen on 2007-07-22
> **Yes said:**
> Right, I chose "Force VESA Drivers", and it worked!  I resized my root partition and can now log into Ubuntu!

Thank you to everyone who helped!

\o/

---

