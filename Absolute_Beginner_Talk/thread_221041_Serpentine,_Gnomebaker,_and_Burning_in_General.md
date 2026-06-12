---
title: "Serpentine, Gnomebaker, and Burning in General"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-07-22
Hello there,

I installed most of my multimedia programs through Automatix, including all of the required codecs (I think).  Yet, when I try to burn a CD with Gnomebaker, it says I don't have mp3 support.  When I try to burn a CD with Serpentine, it says I don't have enough "cache memory."  I am able to burn Audio CDs with Rhythmbox, but it is really slow when converting the mp3s, and on the whole pretty clumsy when burning CDs (I have to create a playlist, etc).  

Any advice for this Ubuntu noob?

---

### Post by kop316 on 2006-07-22
I am not sure how to fix it on gnomebaker, but i found that when you put the CD in the drive, a window pops up offering to make a music CD. that program I found to be better the gnomebaker, and it burned the audio CD with mp3 for me.

---

### Post by croak77 on 2006-07-22
Gnomebaker uses gstreamer-0.8 so install gstreamer0.8-lame and gstreamer0.8-mad.

---

### Post by limberlegs on 2006-07-22
OK, so I'm giving Gnomebaker a shot since I can't find any support for my Serpentine problem.  I installed gstreamer 0.8-mad, and gstreamer 0.8-lame, and I was able to add mp3s to an Audio Disk.  I then had the following problem, outputted by Gnomebaker:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

```

Any thoughts as to why this might have happened?  How do I change the permissions to allow Gnomebaker to burn CDs?  

Perhaps there is a better or equally competent program that will have less trouble doing what I ask?  I was able to get Rhythmbox to burn a CD, but it's a very clumsy process.  Plus, I want a good program to burn DVDs and data disks also.

Thanks for your help in this endeavour!

---

### Post by richbarna on 2006-07-22
I use k3b, it's in the repositories.

---

### Post by limberlegs on 2006-07-22
Ha... OK, I tried K3B, and I apparently don't have mp3 support for it either :)  Shouldn't Automatix have installed all of these codecs already?

Shouldn't I be using a Gnome-based program anyway?  Sorry, that's probably a noob question.  

Perhaps I could just convert all my mp3s to ogg vorbis.  It would cause havoc on my iPod, sadly.

---

### Post by richbarna on 2006-07-22
> **limberlegs said:**
> Ha... OK, I tried K3B, and I apparently don't have mp3 support for it either :)  Shouldn't Automatix have installed all of these codecs already?

Yeah it should of you need to look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by limberlegs on 2006-07-22
Hmm... it seems that I have all of those programs installed already.  I've got:

gstreamer0.10-plugins-ugly
gstreamer0.8-mad
gstreamer0.8-misc

I installed the last two when trying to get Gnomebaker to work, and they did allow me to add mp3s to an Audio CD.  The problem was then it returned the errors I listed above (in #4).

---

### Post by orb9220 on 2006-07-22
Did you say that you installed lame ?

---

### Post by limberlegs on 2006-07-22
I have installed both

gstreamer0.8-lame
lame

Would that cause something to be broken?

---

### Post by croak77 on 2006-07-23
Try running Gnomebaker as root. There was a bug. Don't know if it's been fixed.

Or nautilus-cd-burner.

---

### Post by limberlegs on 2006-07-23
Heh... yeah it worked when I ran:

sudo gnomebaker

from the command line.

Strange, if you ask me, but whatever.  I suppose it's really not that much more effort than clicking on the gnomebaker icon itself.

Is there a way to set the permissions so that I don't have to do this everytime?

---

### Post by JoWilly on 2006-07-23
During all those years, the problem with all these opensource linux burning apps is that very often they suddenly don't work, and you don't know why.

Sometimes its a bug in the app itself, sometimes it the apps it relies on (cdrecord, growisofs, cdrdao, etc...), sometimes something has changed in the kernel,... what a mess.

IMHO the best burning app in linux is nerolinux. It supports the full nero 6.6.4 api and therefore accesses the burner directly.

Nerolinux needs mpg123 and lame to be installed to handle mp3.

---

### Post by wilko on 2006-07-25
Have a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=217472](http://www.ubuntuforums.org/showthread.php?t=217472)

---

### Post by limberlegs on 2006-07-26
Thanks all for your responses!  I will give nerolinux a shot and see if it works.  If not, I will try the more lengthy fix suggested by Wilko.  

Does anyone know why the "conversion" from mp3 to wav that occurs right before the burning an audio CD might occur?  It seems that this was much faster in Windows, but perhaps I don't have everything installed correctly.

---

