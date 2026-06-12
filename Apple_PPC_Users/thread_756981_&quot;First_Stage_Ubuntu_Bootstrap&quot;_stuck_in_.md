---
title: "&quot;First Stage Ubuntu Bootstrap&quot; stuck in loop"
date: 2008-04-16
forum: Apple PPC Users
---

### Post by xelapond on 2008-04-16
Hello, 

I am trying to install Ubuntu 7.04 Server onto a G3 Snow Imac.  When I put the disk in and hold down the C key it shows a black screen with:

> First stage ubuntu bootstrap

l for GNU/Linux
c for cdrom
boot:

I Hit C again, and it displays a white screen.  It then goes back to the same menu.  If I hit l it goes to a menu with yaboot.  I hit enter there, and it says something about a corrupt fielsystem.  I think that is because I tried to install arch, so if formateed it but the network would not work.

Ubuntu HAS worked before on it, so i would think it should work now.  I have tried 2 different disks, Gutsy, Fiesty, two CD Drives(Internal and an external Firewire), and mulpple burns on each disk.

Thanks, 

Alex

---

### Post by stream303 on 2008-04-16
Did you burn at a low speed?  Maybe the burn speed you are using is just on the edge of being unusable on that G4 snow's cdrom...

---

### Post by xelapond on 2008-04-16
I let Braseo auto pick the speed.  It hung around 3.8 to 4.3 X though.

---

### Post by slacka-vt on 2008-04-16
Have you reset the PRAM ?
[command+option+p+r] until it cycles 3 times (you hear 3 boot chimes)
What happens if you hold down [option] key at boot and select the OS or CD from there ?
Sounds to me like yaboot got screwed. 

~s

---

### Post by xelapond on 2008-04-16
I reset the PRAM.  The Font got a little bigger.  When I hit C the first time it looped, but the second time it hung on Loading CDROM...

When I select from the menu it does the same loop, brings me right back to that menu.

Isn't yaboot the bootloader on the hard drive?  Why would that effect the cd booting?

---

### Post by stream303 on 2008-04-17
Maybe I'm missing something here...

When you boot with the CD by holding down "C", you get to a yaboot menu, whereupon you press "L" for Linux.  Or you could just let it time out and it will automatically select linux and move to the second stage.  No need to select CD again here, since you are already booted - hence the loop you are seeing.

At the second stage boot: prompt, you could again just let it time out and it should take you straight into the installer.  If you needed to add special kernel parameters, like *nosplash,* this would be the place to do it, but for now just let it time out and see if the installer comes up automatically.

---

