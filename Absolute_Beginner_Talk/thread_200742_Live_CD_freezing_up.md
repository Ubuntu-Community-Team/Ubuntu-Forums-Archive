---
title: "Live CD freezing up"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by bem on 2006-06-20
I thought it about time I gave ubuntu a go but I'm having problems using the live CD.  So far I have:

Downloaded ubuntu-6.06-desktop-amd64
Verified with md5summer
Burned the CD
Booted from CD and successfully verified the CD
Booted from CD and successfully run memtest86
Booted from CD into Ubuntu live

Everything seems fine for a couple of minutes but then I make a random action which seems to freeze up the OS and I cannot get any response from the system and have to use the reset button.  This has happened 3 times:

Once when switching to a different window while playing the Nelson Mandela video
Once after clicking on the install icon on the desktop
Once when clicking on a different device on the disk drive utility.

I would like to install Ubuntu to hard drive but I'm a little reluctant while I'm having this problem with the Live CD, it doesn't seem normal.

Does anyone have any ideas what the problem could be?  I'm wondering if I should be using the 32 bit version but I cannot see why the 64 shouldn't work.
I have a Sempron 64 3100+ CPU.

Many thanks

---

### Post by taurus on 2006-06-20
How fast did you burn the ISO image?  Maybe you want to burn it again except this time, go with 4x instead...

---

### Post by bem on 2006-06-21
I buned the CD using the default speed so I guess it probably used the fastest.  I will try again at 4x this evening.  Thanks for the help.

---

### Post by acht on 2006-06-21
could also be that your cd-rom isn't very good or is messed up.  how old is it?

---

### Post by bem on 2006-06-21
The CD/DVD writer is new, I have only had it a couple of weeks.  It is a Shuttle CR40.  I did have problems booting from CD to install Windows XP but I put that down to the CD-R I was installing from - once I got it to boot, Windows installed fine.

I've tried burning more Ubuntu CD's but am not having any luck.
The original was done using burnatonce at x16, I tried at x8 (the lowest speed available) but got the same results.
Then tried installing CDBurnerXP Pro and burned at x1 but ubuntu didn't even finish loading the desktop before freezing, I rebooted and it froze loading a game.  Tried different media at x4 but had freezing problems again, and this time there was a checksum error.  Tried another make of CD-R at x1 but got CD Writing Error (3).

I think I am going to download the iso again (the 32bit version) and try burning using the Nero OEM software that came bundled with the CD drive (although slowest write available is x8 ).  If anyone has any better ideas I'd be grateful to hear them.  Thanks again.

---

### Post by bem on 2006-06-24
Well I finally got ubuntu running, it looks like it was a graphics problem in the end - the 32-bit version wouldn't load the gui at all, so I tried starting in safe graphics mode and everthing worked fine.  When I went back to the original 64-bit CD I made, safe graphics mode worked fine with that too.

It's now installed to hard drive and it all seems to be working okay.  The only thing I've noticed is that the graphics are a bit jerky sometimes.  Not sure where to start there but it's not really a problem at the moment.

---

### Post by h2oclick on 2006-06-24
how much memory do you possibly have?? and what video card.... jerkyness can lead to crappy video card and next to no memory

---

### Post by jimrz on 2006-06-24
[QUOTE=bem]I thought it about time I gave ubuntu a go but I'm having problems using the live CD.  So far I have:

Downloaded ubuntu-6.06-desktop-amd64
Verified with md5summer
Burned the CD
Booted from CD and successfully verified the CD
Booted from CD and successfully run memtest86
Booted from CD into Ubuntu live

Everything seems fine for a couple of minutes but then I make a random action which seems to freeze up the OS and I cannot get any response from the system and have to use the reset button.  This has happened 3 times:

Once when switching to a different window while playing the Nelson Mandela video
Once after clicking on the install icon on the desktop
Once when clicking on a different device on the disk drive utility.

I would like to install Ubuntu to hard drive but I'm a little reluctant while I'm having this problem with the Live CD, it doesn't seem normal.

Does anyone have any ideas what the problem could be?  I'm wondering if I should be using the 32 bit version but I cannot see why the 64 shouldn't work.
I have a Sempron 64 3100+ CPU.

Many thanks[/QUOTE]

had similar issue with the "live" cd...downloaded the "alternate" cd and did the install from it...got the correct driver for my nvidia card via Synaptic...now all is working as it should.  had previously installed dapper rc to my laptop using the "alternate" and basically the same proceedure (except that it has ATI video so had to get a different driver) and it, too, is all good

---

### Post by bem on 2006-06-25
System memory is 1GB, video is on-board (Via K8M800 Unichrome pro).  The BIOS was set to use 32MB shared video RAM, changing to 64MB hasn't made any noticeable difference.

Doing a search on Synaptic shows there is a driver installed for this chipset, whether it is the ideal one I don't know but there are no alternatives displayed there.   A driver issue was my first thought but I think I will have to wait until I am a bit more familiar with Linux before delving into anything like that.

In the meantime if anyone has any other straight forward suggestions I would appreciate it, thanks.

---

