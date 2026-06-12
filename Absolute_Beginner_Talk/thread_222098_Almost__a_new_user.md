---
title: "Almost  a new user"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by welshman on 2006-07-24
Trying to install ubuntu ! System had MS win98.formatted disc
then started computer with cdrom support tried to run Ubuntu install disc.not a lot happened. I get thr impression the cd is not being recognized (cd is Atapi drive ) any suggestions for a dim wit

---

### Post by T700 on 2006-07-24
First suggestion:  Don't call yourself names.  There are plenty of people in world ready to run you down.  Don't give them any help.

Next, are you ***sure*** you have a good install disk?  If you burned it, did you burn it as an ISO image--not a copy and not a bootable disk?  Is your computer set to boot from CD?  **To use the Ubuntu disk, you must put it in and boot with it in place.  Do not start the PC with Windows 98 first.**

Please describe exactly what is happening and what you're seeing during the failed boot process.

By the way, welcome to the forum!

Paul

---

### Post by Optiker on 2006-07-24
Since it's Win98, I'm assuming it might be an older computer. I had one that didn't support booting from CD. The thread at [http://www.ubuntuforums.org/showthread.php?t=145212](http://www.ubuntuforums.org/showthread.php?t=145212) covers my questions here and the eventual solution. Here's the reply from rattking that suggested using Freedos boot disk that includes the option for booting from CD...
-------------------------
[I]I have an idea.. on the Freedos boot disk there is an option for Smart Boot Manager.. this supports booting from cd and many others
download the floppy image here
[http://www.ibiblio.org/pub/micro/pc-...2/fdos1440.img](http://www.ibiblio.org/pub/micro/pc-...2/fdos1440.img)
you can write the image to a floppy with the command
dd if=fdos1440.img of=/dev/fd0
boot that floppy and choose option 2 Smart Boot manager
select CD-ROM from the boot menu
and hopefully your system will boot from cd
good luck[/I]
---------------------------
The command he gives is a Linux command line command, so not relevant since you don't yet have Linux installed. The next question was how to write a floppy img to floppy, and that answer was to use one of the Rawrite utilities at [http://www.fdos.org/ripcord/rawrite/](http://www.fdos.org/ripcord/rawrite/). Here's the message in that thread where I reported my success with the needed info...
---------------------------
*Based on the recommendations on the fdos site, used RawWriteWin to write the img to floppy, ran the utility, and shazam! Worked great! Kubuntu installed and other than the typical problems with sound and getting all of the right partitions seen and mounted, looking good! It runs a bit slow as one might expect from a 200 MHz cpu! But, still, will do fine for the intended purposes.*
---------------------------
So...seems complicated, but I'm not an expert either and was able to work through it, and it actually did what it was supposed to do. If you get to where you aren't able to boot from CD and out of easier options, you might try this.

Optiker

---

### Post by djsroknrol on 2006-07-24
Are you trying to run the CD off of a Win bootup diskette?..it sounds like it...you need to go into your BIOS and set the CD-ROM to boot first if you are trying to install it..I don't think that way will work...;)

---

### Post by Optiker on 2006-07-24
> **djsroknrol said:**
> Are you trying to run the CD off of a Win bootup diskette?..it sounds like it...you need to go into your BIOS and set the CD-ROM to boot first if you are trying to install it..I don't think that way will work...;)

With an older system, sometimes booting from CD is not possible. My previous post describes how to get around that - Smart Boot Manager is a floppy-based boot manager that implements boot-from-CD as an option, even if you aren't able to set BIOS to do that. Setting boot-from-CD in BIOS is, of course, the obvious first and simpler option. What I described is only a fallback if you can't set it in BIOS.

From personal experience, it works!

Optiker

---

### Post by welshman on 2006-07-25
The cd I am using is a ISOimage from Ubuntu
when I boot I get the message
VERIFING DMI POOL DATA.....flashing cursor.
CD light is on cd sounds as if it is trying to read disc
computer then halts with unaltered message.
does this help

Bill

---

### Post by MaximB on 2006-07-25
what PC do you have ? CPU,ram,HD...

---

### Post by welshman on 2006-07-28
Thanks for imput solved my problem. I am now a new user.
Replaced cdrom with a newer one disc installed like a dream

Thanks again..

Bill

---

### Post by T700 on 2006-07-28
> **welshman said:**
> Thanks for imput solved my problem. I am now a new user.
Replaced cdrom with a newer one disc installed like a dream

Thanks again..

Bill

Great!  Thanks for posting back with the resolution.

Paul

---

