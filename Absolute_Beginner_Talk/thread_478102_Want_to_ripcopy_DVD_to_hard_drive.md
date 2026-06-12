---
title: "Want to rip/copy DVD to hard drive"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-19
Hello,
There is a DVD movie in my disc drive. What is the simplest, most-newbie friendly way of getting the DVD onto my hard drive? I want to be able to play the movie from my hard drive, without the DVD disc being in the disc drive.

I prefer to have all the functionalities of the DVD (such as the subtitles, audio commentary) if it's not going to add too much hassle.

I prefer not to clutter my hard drive with too many files/programs that will just take up unnecessary hard drive space and RAM (as found in "top").

Thank you.

---

### Post by Hund on 2007-06-19
I use dvd::rip.

---

### Post by joe.turion64x2 on 2007-06-19
You want to make an ISO image of your disk,  wise idea. Perhaps you'll need an app called makeisofs. An alternate method is to directly copy it, supposing the drive is in the devices /dev/dvd, type in a terminal: **cp /dev/dvd file.iso** where file.iso is the name of the ISO image you are about to create. I think you need to have libdvdcss installed and to try to do this while the disk is unmounted.

Joe.

---

### Post by hanzj on 2007-06-19
Hund, I did get dvd::rip. When I first opened the program, it brings me to the Preferences, so that I could set things up. On the second tab, Commands, there are 4 lines which use 3 programs: mplayer, xine, and rar-2.80. Do I need those 3? Don't I have anything on my freshly installed Ubuntu 7.04 that can replace one, 2, or all 3? Thank you.

---

### Post by hanzj on 2007-06-19
I installed mplayer (through synaptic), as it seems to be _the_ media player for ubuntu. It's geared for pros apparently: It's a CLI program. How can one use mplayer to rip a DVD for hard drive viewing?

---

### Post by tekhawk on 2007-10-31
you dont use mplayer to do it you use dvd:rip it will interface with those 3 programs to get the job done for you.. you will need all 3 of those programs installed also there is a gui you can install for mplayer open up your preffered package manager and search for mplayer install ALL mplayer related packages its just flat a good idea if you dont want to worry about playing some odd ball media format later on..

just rip the secections you want through dvd rip and play them through mplayer if you want but get its gui first.. good luck have fun : )

btw can you play the dvd on your system yet if not your going to need to tackle that first

---

### Post by andrew.46 on 2007-10-31
Hi,

 Saw your problems with dvds:

> **hanzj said:**
> I installed mplayer (through synaptic), as it seems to be _the_ media player for ubuntu. It's geared for pros apparently: It's a CLI program. How can one use mplayer to rip a DVD for hard drive viewing?

With mplayer you can't rip the entire dvd but you can certainly rip complete titles. Straight from the man pages:

> Copy a DVD title to hard disk, saving to file title1.vob :
mplayer dvd://1 -dumpstream -dumpfile title1.vob

But there is a better way to copy the entire dvd by using vobcopy. If the movie is encrypted you will also need libdvdcss:

```
vobcopy -v -m /media/cdrom0
```

This copies the entire movie (-m is mirror) from your drive (/media/cdrom0) in verbose fashion (-v) to the directory from which you issued the command.

For the record although mplayer is a command line program it has a gui called gmplayer which may be a little friendlier for you :-)

     Andrew

---

### Post by thrag on 2008-02-22
> **Hund said:**
> I use dvd::rip.

I think the question was for an EASY tool to rip a DVD to hard drive.

dvd::rip is the absolute worst (counter-intuitive) piece of software I have every used.  I am still unable to rip a DVD to hard drive, and I have been working on this program for 3 hours.  What a mess.  It may be great for those who want TOTAL control of the process, but I simply want to rip a DVD to hard drive!  Where is the simplicity?!??!!

---

### Post by mc4man on 2008-02-22
For absolute simplicity try vobcopy - 1.1.0 or 1.0.2 are improved over repo ver.
```
vobcopy -v -m -F 16 /media/cdrom0
``` is a good basic comm.

---

### Post by halitech on 2008-02-23
If size is not an issue, you could use K3B to copy it and just select to make an image only and that will create an exact image in ISO format and then you can use VLC to play it. If the DVD is bigger then 4.4gig, you will need to actually rip if you want to burn it again unless you have a dual layer burner and dvds.

---

### Post by rfurman24 on 2008-02-23
I personally feel k9copy is the easiest. It will even allow you to shrink it. I just through in the dvd and rip it to iso.

---

### Post by jurgenfauth on 2008-03-29
k9copy crashes on my 7.10 install -- not sure why.

With dvd::rip, I can copy the main title to a vob file, but I'm not sure how to clone the entire disc. Is there a painless way to copy an entire DVD to the hard drive as VOB with dvd::rip?

---

### Post by joe.turion64x2 on 2008-03-29
I use to copy full DVDs by rightclicking them and selecting Copy Disc (I use GNOME), then I can either create an ISO or physically copy the DVD into another one.

---

### Post by jurgenfauth on 2008-03-30
Works for me -- thanks!

---

### Post by jurgenfauth on 2008-03-30
Actually, that doesn't quite work because it creates an ISO, which most of the other programs -- dvd::rip, AcidRip, or DVD Shrink -- can't seem to do much with. They all want VOB files for input, from what I can tell.

So, what's the easiest way to copy all VOB files to a hard drive? Can I simply move the  VIDEO_TS folder by hand?

---

