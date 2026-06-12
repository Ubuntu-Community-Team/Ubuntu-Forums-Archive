---
title: "From AVI to DVD- should it be this obtuse?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-07-04
Keeping it simple, here is my situation, problem, and goal:

1: I have a .avi file

2: I would like a DVD to play said .avi file in my friend's dvd player.

3: I don't use Terminal for more than downloading as I don't understand all the commands (I'm reading up on how to do this). That being said, I would like to find a GUI frontend that will work for me.

4: How do I get .avi to .mpeg2 format?

5: I have K3b and it looks pretty straightforward but I believe I'll need audio and video (though I've read that the audio.ts folder is not really used any more.). 

6: Can I find a nice non-terminal based program to convert my files 

and 

7: Will I need to somehow split my video and audio? 

This really shouldn't be this hard....
I have ffmpeg and widencode (I think?) and mencode and sox but have no idea how to do this. I would like to use this T@B media converter i found but it's in a tar.gz format and I can't find a straightforward guide on how to compile something.

thanks

---

### Post by moore.bryan on 2007-07-04
*it's so involved because of proprietary formats and such.  the most straight-forward way i found is [here]("http://ubuntuforums.org/showthread.php?t=487513").  there's also a decent-looking walkthough [here]("http://doc.gwos.org/index.php/Dvd_Videos_From_An_Avi_File").*

---

### Post by avik on 2007-07-04
I can't answer all your questions, but I'll try my best.

> Keeping it simple, here is my situation, problem, and goal:

1: I have a .avi file

2: I would like a DVD to play said .avi file in my friend's dvd player.

3: I don't use Terminal for more than downloading as I don't understand all the commands (I'm reading up on how to do this). That being said, I would like to find a GUI frontend that will work for me.

4: How do I get .avi to .mpeg2 format?


As you have figured out, the file needs to be in MPEG format, and I know you said you would prefer a GUI, I know you can use the following command (found in the [MEncoder Manual]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-mpeg.html")):

```
mencoder *input.avi* -of mpeg -mpegopts format=mpeg1:tsaf:muxrate=2000  -o *output.mpg* -oac lavc -lavcoptc acodec=mp2:abitrate=224 -ovc lavc -lavcopts vcodec=mpeg1video:vbitrate=1152:keyint=15:mbd=2:aspect=4/3

```

> 
5: I have K3b and it looks pretty straightforward but I believe I'll need audio and video (though I've read that the audio.ts folder is not really used any more.). 

...

7: Will I need to somehow split my video and audio? 


I've used DVDStyler in the past because of its simplicity.  You can get it at [here]("http://www.getdeb.net/app.php?name=DVDStyler").  You don't need separate video and audio, as the MPEG file will work.

---

### Post by Protagonistics on 2007-07-04
It's not working. I'm using ffmpeg in the terminal and I'm getting this response. I uninstalled and reinstalled ffmpeg and the message did not change.

ffmpeg -i Humans Vs Zombies Documentary.avi -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd Humans Vs Zombies Documentary.mpeg

ugh.

---

### Post by michaelzap on 2007-07-04
I use Avidemux to create an mpg2 video with ac3 audio and then ManDVD to create the DVD structure. You can also use DeVeDe to do it all in one step. All of these are GUI programs, and there are a number of guides for using them around.

---

### Post by Ssj3_man on 2007-07-06
first choice is WinAVI for windows (will Wine run it?)
second is [http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/) does a decent job for me one unexplained skip.

---

### Post by moore.bryan on 2007-07-06
> **Protagonistics said:**
> It's not working. I'm using ffmpeg in the terminal and I'm getting this response. I uninstalled and reinstalled ffmpeg and the message did not change.

ffmpeg -i Humans Vs Zombies Documentary.avi -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd Humans Vs Zombies Documentary.mpeg

ugh.
*the title needs to not have spaces OR must be quoted... perhaps that's the issue.*

---

### Post by blackened on 2007-07-06
As Senor Moore said, because the filename contains spaces you need to either 1) rename the file to something like HumansVsZombies.avi or 2) use quotes to contain the filename a la 'Humans Vs Zombies Documentary'. The end result will be a command that looks like either

```
fmpeg -i HumansVsZombies.avi -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd HumansVsZombies.mpeg
```
or
```
fmpeg -i 'Humans Vs Zombies Documentary.avi' -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd 'Humans Vs Zombies Documentary.mpeg'
```

---

### Post by moore.bryan on 2007-07-06
*mucho gracias, amable señor ennegrecer.*

---

### Post by Digitallysick on 2007-07-06
the easy way

[http://www.getdeb.net/download.php?release=1106&fpos=0](http://www.getdeb.net/download.php?release=1106&fpos=0)

download this and install it

---

### Post by Ssj3_man on 2007-07-06
> **Digitallysick said:**
> the easy way

[http://www.getdeb.net/download.php?release=1106&fpos=0](http://www.getdeb.net/download.php?release=1106&fpos=0)

download this and install it

Yah then burn that ISO file to a DVD, with K3b or an burn agent that can burn ISO's.  ;)

---

### Post by Plissken@plissken on 2008-01-13
all you have to do is install devede open it choose video dvd drop your avi. movie in the right box where it says file. press forward then OK it will start converting the iso image when it's done if you have k3b installed open it up go to further actions... and choose new video dvd project. pick  your cd or dvd drive in the left of your screen thats if you have 2 or more then your iso image should be in your home folder click on the iso image drag and drop it in video ts directory burn image directly and there you go a movie that will play in your regular house hold dvd player. i hope it will work for you becaused it worked for me i've been only been using ubuntu for the past year and it's way better than windblows if my post does not work keep looking you'll eventually find one that will work for you

---

### Post by zebralinux on 2008-01-13
Use  gui based application devede !
 search for devede in synaptics.
[http://www.rastersoft.com/programas/devede.html]("http://www.rastersoft.com/programas/devede.html")

---

### Post by xavier0499 on 2008-01-15
thank you for your guide...I'm also new to Ubuntu from Windows and I'm very  please with the whole experience....I'm going to convert my 3 computers to Linux and only use windows when absolutely necessary..... 

Thank you all again for all your help!!!

---

### Post by xavier0499 on 2008-01-24
I've been trying to burn an avi movie file to a DVD that can be played on any DVD player for the last week....

I'm running Ubuntu 7.10 and I first turned the AVI file to ISO using DeVede. I them tried burning the ISO using K3B but I keep getting this error...

COULD NOT DETERMINE SIZE OF RESULTING IMAGE

below is the debugging output file:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HP DVD Writer 400c KH27 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW] [DVD-ROM, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R]

JLMS XJ-HD166S DPS7 (/dev/scd1, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.6

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-xavier/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
/usr/bin/genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-xavier/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Ratatouille -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-xavier/k3bErOx5b.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-xavier/k3b8pbs6a.tmp -dvd-video -f /tmp/kde-xavier/k3bVideoDvd0 

any help is much appreciated...

thanks

---

### Post by doorknob60 on 2008-01-24
Hmm...maybe try with another program like gnomebaker or gnome's built in burner?

---

### Post by xavier0499 on 2008-01-24
doorknob60 thanks for your quick response... I tried the built in ISO writer but the disk could not be read by my DVD player.... I'm trying gnomebaker now..I'll let you know how it goes,

---

### Post by xavier0499 on 2008-01-24
burned the ISO with gnomebaker but my DVD player still won't read the DVD.... The file burned correctly but it's not playing as a DVD....


Thanks

---

### Post by Emerzen on 2008-01-24
I've had the most success with AVIdemux.  It's GUI based and pretty simple.

First, open the AVI, then on the left hand side, under video, select "DVD/Mpeg2." (I also suggest using 2 pass under configure--takes longer though)

Under audio select wavPCM

Then hit save-->you'll get an MPEG2 file.  Open DeVeDe and follow the create DVD menu and import the MPeg2.  When it's done use K3B or gnomebaker to burn the ISO.

I've found this often works even when things like Nero (in windows) fails.

---

### Post by xavier0499 on 2008-01-24
I'll give this a try...... I'll post my finding tomorrow...

Thanks

---

### Post by cysco24 on 2008-03-07
I tried Devede and didn't work for me.  Since I was in a rush I gave ConvertXtoDvd windows program on wine.  It worked with no errors.   I havn't tried to burn to disk with it but in the end I get a Video_ts folder that i can burn with k3b.

Or I can use Folder2iso (also a windows program that works with wine) to convert that video_ts to an iso file.

---

