---
title: "gparted help"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-17
i need help in increasing the ntfs window patition in order to finish a torrent donwload 
further detail can be refer to here [http://ubuntuforums.org/showthread.php?t=503320](http://ubuntuforums.org/showthread.php?t=503320)
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-3.png[/IMG]

---

### Post by AlexenderReez on 2007-07-17
how about try partition magic ...as far i know it can cut one partition to become to without moving its files...but i don't really sure whether it can  be use to combine 2 separate partition without disturbing file inside or not...

---

### Post by zerobinary on 2007-07-17
anyone idea

---

### Post by ramjet_1953 on 2007-07-17
You cannot re-size a partition if it is mounted.

There are two ways to overcome this:

1. Boot from the LiveCD and run parted from that.

2. Download the GParted iso and burn the CD

You can get the iso from here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I prefer the second option myself.

If you decide to go this way, don't forget to burn it as an iso and burn SLOWLY, no faster than 4 X.

Regards,
Roger

---

### Post by zerobinary on 2007-07-17
i will go into live cd but how do i resize it properly need help on that

---

### Post by glennric on 2007-07-17
> **ramjet_1953 said:**
> 
2. Download the GParted iso and burn the CD

If you decide to go this way, don't forget to burn it as an iso and burn SLOWLY, no faster than 4 X.

Regards,
Roger

Why must you burn it at a speed no faster than 4X?  What difference will that make?

---

### Post by zerobinary on 2007-07-17
i guess safer 
but help with gparted 
i don't want to resize it wrong to kill my download

---

### Post by Rocket2DMn on 2007-07-17
You're gonna have to cut into your /dev/sda3 (your linux stuff), but you don't have much on there so it should work out OK.  Expanding the space on your ntfs driver where your torrent is shouldn't kill your download.
I've never repartitioned like this before so that is all the help I can offer you.  Good luck.

---

### Post by zerobinary on 2007-07-17
err not working 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-8.png[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-4.png[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-2-2.png[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-3-2.png[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-4-1.png[/IMG]

---

### Post by zerobinary on 2007-07-18
nevermind i screw up the whole thing

---

### Post by jamieh on 2007-07-18
You can't resize a hard drive that your currently running OS is on, here's what you do:
[URL="http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-8.iso?modtime=1182962209&big_mirror=0"]
1) Download this file[/URL]

2) Burn the ISO to a CD, if you don't have an ISO burner, I like [this one]("http://isorecorder.alexfeinman.com/isorecorder.htm"), it is 100% free.

3) Boot from the CD and edit your partitions as desired.

If you need any more help, just P.M. me.

J.

---

### Post by dptxp on 2007-07-18
Why do you not move some files to another partition to create space ?

---

