---
title: "Playing CDs in XMMS"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-24
Well I've been trying to get everything working, and I've wound down my problems to very few. My current problem is that I cannot use XMMS (My media player of choice :D) to play CDs. 

I try to use "Play Directory" to play every directory I can think of (/dev/cdrom, /cdrom, /media/cdrom0) but nothing works. I'm probably doing something wrong, can anyone help me out here? I've searched the forums and Google for three hours or so now with no luck.

---

### Post by bodhi.zazen on 2006-12-25
Not to ask the obvious, but did you install the proper restricted formats ?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

What type of CD ? Music, MP3 ?

Then insert the CD -> it should mount.

Right click on XMMS -> Play Directory -> navigate to you mount point.

/media/cdrom, /media/cdrom0, what have you.

If you do not know, look in /media 

HTH

---

### Post by Pobega on 2006-12-25
I did everything in that help.ubuntu.com page, and it still doesn't want to work. The problem is that I can't find any .mp3 files, so I have no clue where they are!

Edit: This is a purchased album, so I am not sure everything will be in .mp3 format. I've never actually looked at any CD's contents before (On WIndows), so I wouldn't know.

---

### Post by LoneStarSamurai on 2007-04-11
With XMMS, you will a: need to make sure that it's set to be able to read and play cda format (as opposed to mp3, ogg, etc).  The how of that depends on whether or not you have a physical audio cable for your cdrom;)

Assuming that you DO have that set up, you would then need to choose "Play File" in XMMS, and then add your cd (default is typically /dev/cdrom). 

If you do not have the cd playback configured for XMMS then by all means let me or someone know, and we can help, I'm sure.

(I say all this, because I just got all that set up for XMMS. Configuring it under Fedora was a tad simpler. But whatever.)

---

### Post by Mujaheiden on 2007-04-18
So this is what to do 

$sudo apt-get install xmms-cdread

open xmms

go to Preferences (CTRL-P)

Select Audio I/O Plugins (make sure it is clicked as enabled)

Select CD Audio Player 

Select Configure

Configure the thing

and it should work - if you confiugerd it properly, that is (does for me)

---

### Post by meborc on 2007-04-18
i usually open nautilus and drag the files on CD to the playlist...

---

