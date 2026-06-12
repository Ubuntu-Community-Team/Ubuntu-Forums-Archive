---
title: "device names"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by John Macnab on 2007-07-28
Hi
In the Places>My Computer section , it shows my partition where windows is installed as sda1. But the File System icon, the floppy and my two CD drives do not show any device names.How do I find their device names please?The cd drives are supposed to be named scd0 and scd1 arent they?

---

### Post by encompass on 2007-07-28
Why?
Well unless you want to get technical with things like special mounting things, I don't see a reason for you to worry.  None-the-less:
take a look at this location. /dev/
in there you have many different devices to work with.
In our case we have a sata device for your harddrives... so sda is the first device sdb the second and so on.  Where the devices are mounted and used is a whole nother issue.
And yes... your cd rom looks like it is scd0
Other devices to look for are ide drives.  Those are hda, hdb, and so on.
Does that answer it?
If you use the lshw command it will show you all your hardware and where it is plugged in.

---

### Post by John Macnab on 2007-07-28
Sorry sir but I was trying to play VCD's and I came across some advice on the forum about installing CDFS and then mounting the VCD using command line. So I thought I'd need to know the device name of the cd drive I am putting the CD in( I have a DVD writer and a CD drive).
Thank you for explaining sir.I was just wondering about the other drives, as the partition where Windows is,is shown as sda1 so was thinking why the other partition where not shown. I had partitioned the rest of my hard drive into /, /home and swap and I puzzled over why those partitions werent named or shown-the only other hard drive icon was "file system" which I suppose includes all three linux partitions?

---

### Post by encompass on 2007-07-28
In a way your right with the sda1 that is your windows partitions.  But it simply a name, nothing more.
You also have in your /dev/ sda2,3 and so on for all of your partitions (I think your swap is even there)
As for what your doing.  I have no idea what they are wanting to do with it.  But movie player can't play them?  Does it give any errors?

---

### Post by encompass on 2007-07-28
Oh and is this a DVD like one that you purchase from the store?

---

### Post by John Macnab on 2007-07-28
Hi
Yes sir, the DVD and the VCD's are all store purchased.All those VCD's come with movie file in .dat format- like avseq01.dat. And in Windows, it does play right away but not in Ubuntu.In fact the VCD's wouldnt even get recognized until I installed CDFS. As for the error messages sir, Totem says :Totem could not play 'vcd:///media/cdrom0, and: there is no input plugin to handle the location of this movie.
 Xine says there is no demuxer plugin to handle avseq01.dat
In VLC it asks for the device name and it already has scd0 put in, so I didnt do anything there but it doesnt even try to access the drive, it seems- not even when I try to play the file alone instead of the VCD.
With Mplayer, if I try the file alone, it says 'seek failed',If I try playing the VCD as a whole, it just says: error opening/initializing the video_out device

---

### Post by encompass on 2007-07-29
Alrighty,
Have you installed the codecs for playing DVD's and other formats?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
Take a look there... it may help you out.
That is what did it for me.

---

### Post by John Macnab on 2007-07-29
Hello
Yes sir, I had installed the codecs mentioned in the page you provided and my DVD does play but its my VCD's that just wont play no matter which movie player I use

---

### Post by encompass on 2007-07-29
Wish I could help you more.  But I don't know video that well.  Sorry.

---

### Post by John Macnab on 2007-07-29
Oh no problem sir.Thank you for trying to help :) I appreciate that

---

