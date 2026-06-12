---
title: "Ubuntu on AMD machine"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-04-07
Hi I have been having problems with my amd machine when it had ubuntu6.10 on it and finally it is now not working. The mouse is frozen. So my question is if I put another hd in the same pc with ubuntu on it so I can retrieve some files off the original drive then how do I install the correct version of ubuntu on it. One friend said that I may have had many problems with the system because i installed from the cd and it defaults to the lowest version which is intel. The other thing is with the AMD thing is that it is an xp2000 and I don't think it is an amd64 . Not that I know what an amd64 is but I think it is a new thing and my machine is at least 2.5 years. I wanna get it right.

---

### Post by mikeyphi on 2007-04-07
AMD/Intel CPU makes no difference!
Probably best to use the 32bit version

but more important is what sort of problems did you have?

---

### Post by dwblas on 2007-04-07
I have an AMD64 and have both a 32 bit (intel) and a 64 bit system on it.  It will run either just fine.  I don't think there is a 64 bit ubuntu 6.10, so you have a 32 bit system.  The mouse not working may have more to do with the mouse than the CPU.  If you have another mouse I would try that first.

---

### Post by rapattack1 on 2007-04-08
I think I had Ubuntu installed for a good month and there was first a time/date issue that never got resolved, then sound was never really good, then the dya the mouse froze not allowing me to navigate. It is not the mouse by the way as ubuntu was on one drive and windoze on the other which is what I am back to now. Apart from that I can't think of anything else thta went wrong. I had installed a lot of software and everything ese was working well.
As per the 32bit and 64 bit well I just installed ubuntu on another drive a couple of hours ago with the same amd machine and it stuffed up straight away with first the time/date issue. The bios is correct if that is on your mind and the crappy old windoze drive is correct also. Despite these problems I am still determined to use ubuntu on my primary box as I have it working beautifully on an old laptop. I wish I could use the laptop on the net but it is just too awkward for me as the kb doesn't keep up with my fast typing speeds. I know I can adjust the strick rate but the kb on lappies is just wrong.

---

### Post by hardyn on 2007-04-08
the XP class of athons are all 32bit (yes there was a 64bit edgy).

My moms machine is an athlon xp2400 running edgy, with an ATI 9800pro with open source drivers, works very well.

you can back up the old data buy installing ubuntu on the new disk, then connecting the old drive as a slave or to the other IDE port, mounting and coping.

if you have an exisitng external drive, crack it open and swap the original external drive with the one that you want to back up.  If you think you might want an external drive, buy caddy, and do your backup that way.

good luck.

---

### Post by rapattack1 on 2007-04-08
Yep I had a spare drive and installed ubuntu on it yesterday. Made it a master and the frozen drive a slave but unfortunately the master didn't see the slave at all so I dunno what to do because I am broke and can't afford one of those caddies. Someone suggested that I could do a burn from the command line but didn't give me the details on how to do it.
Funny thing is the first thing that went wrong when installing Ubuntu on this machine with the drive I did yesterday was the same thing that went wrong with the original ubuntu drive that is frozen. Which is the time is incorrect. This is not because of the bios as I had a dual boot situation and windoze reads the time correctly. Something is very odd.

I wish I could retrieve the files with my usb flash stick. That would be really helpful. Maybe from the command line. I dunno.

---

### Post by hardyn on 2007-04-08
im sure you can, but i have never mounted a USB stick from the commandline before, im sure it has been posed on how to do this.

it won't see the drive automatically... you will have to mount it.

sudo mount /dev/hdb1 /<mountpoint>

of course you will have to adjust that to meet your system.

by frozen drive? how are you defining that?

---

### Post by rapattack1 on 2007-04-09
Ok the frozen drive is the mouse is frozen. The mouse is ok as I am using it now with the windoze drive. 
OK will try mounting the drive tomorrow and get back to you on that. What am I supposed to see if I am successful and what would mean a failure? I have never done this so I don't know.

---

### Post by bluedalmatian on 2007-04-09
try running the X setup utility from the command line and get it to re-detect everything including your mouse:

sudo dkpkg-reconfigure xserver-xorg

---

### Post by rapattack1 on 2007-04-10
Will try that soon and let you know. I haven't got the drive hooked up at the moment and no time to do anything. Thanks

---

### Post by rapattack1 on 2007-04-15
bluedalmatian- I got some error when trying to run that command so that didn't work.

hardyn-I dunno yours didn't work either. Was I supposed to put something in place of mountpoint? I dunno what I am doing I am afraid.

---

### Post by hardyn on 2007-04-15
you may want to read up on that...  yes you do need a mount point

you must create a place to address the drive, instead of saying d: or e: we have to make a directory.

so in your home directory on your live disk, (you are going to have to use the command line)

mkdir usbdisk

mount /dev/sdb1 usbdisk

cd usbdisk

if all worked well you will get an icon on your desktop, i will magically appear.

now the sdb1, it totally a guess on my part, i have no idea what flash drive will be, it will vary from system to system.  you may want to read up on this forum for manually mounting a usb disk.

good luck.

---

### Post by hardyn on 2007-04-15
> **bluedalmatian said:**
> try running the X setup utility from the command line and get it to re-detect everything including your mouse:

sudo dkpkg-reconfigure xserver-xorg

dpkg

that is why you got your error.

---

### Post by rapattack1 on 2007-04-15
Yep I tried dpkg as I suspected that was a typo.

Um I am confused. I do not need the usb flash drive if I am able to get the primary working drive to see the slave mouse frozen one. So there is no need for the primary drive to see it if you get my point. I brought up the usb stick originally because I didn't have the primary drive set up like I do now.

---

