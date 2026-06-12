---
title: "Program to resize partitons?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by battleroyalex on 2006-07-04
My 7GB linux partiton isnt holding up anymore I need more space. Is there a program to make my windows partiton smaller and my linux partiton bigger. Like the one that came up while I was installing ubuntu?

---

### Post by Average_Joe on 2006-07-04
[QUOTE=battleroyalex]My 7GB linux partiton isnt holding up anymore I need more space. Is there a program to make my windows partiton smaller and my linux partiton bigger. Like the one that came up while I was installing ubuntu?[/QUOTE]

For that, I used the GParted LiveCD (bootable CD image).
Here's the link I used for the CD image, which I burned within the last 48 hours:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Kobalt on 2006-07-04
Hello,

Yes, you can resize your windows partition. First of all, unfragment it. Then, reboot your computer with a Live CD of Ubuntu in your drive (so that it boots on the Live CD). When you're using the Live CD, there's a tool named GParted (you can find it in the menu, I can't remember if it's Applications or Administration...) : it is what you need to resize, delete, move partitions... 

Cheers !

---

### Post by atoponce on 2006-07-04
[quote=battleroyalex]My 7GB linux partiton isnt holding up anymore I need more space. Is there a program to make my windows partiton smaller and my linux partiton bigger. Like the one that came up while I was installing ubuntu?[/quote] GParted is probably what you are looking for.  It is included in the Desktop CD (Live), and is really good.  A couple of points, though.  You will need to defrag your Windows partition 3 or 4 times to move the data to the front of the partition before you partition, assuming that Windows is the first parition (physically at the beginning of the drive) and Linux is the second.

---

### Post by battleroyalex on 2006-07-04
Gparted does not work, I tried installing it on this EVERYTHING is grayed out.

I tried booting it from the ubuntu CD it lets me resize the windows partiton smaller but then it won't let me resize the linux partiton any bigger with the allicoated space what the hell!:neutral:

---

### Post by aysiu on 2006-07-04
I use DiskDrake on the PCLinuxOS live CD. It's never given me greyed out options.

---

### Post by battleroyalex on 2006-07-04
is disdrake on the ubuntu cd?

---

### Post by aysiu on 2006-07-04
[QUOTE=battleroyalex]is disdrake on the ubuntu cd?[/QUOTE]
No, but I've found it's worth downloading PCLinuxOS just to have a partitioning program that always works.

---

### Post by battleroyalex on 2006-07-04
ack thats no help to me then :(. I keep trying windows partiton magic but it sucks it comes up with an error everytime

---

### Post by battleroyalex on 2006-07-04
agh it seems like NOTHING is working. I just tried gpart just to resize my windows partiton and it says its doing it.. then it flashes back to the screen I started at and its still the same size.. :confused:

---

### Post by Apple 101 on 2006-07-04
[QUOTE=battleroyalex]agh it seems like NOTHING is working. I just tried gpart just to resize my windows partiton and it says its doing it.. then it flashes back to the screen I started at and its still the same size.. :confused:[/QUOTE]
Do you get a particular error?

---

