---
title: "Help....nothing works!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by haruspex on 2007-08-23
I finally got my computer back yesterday, complete with feisty, but nothing seems to work right. I got mplayer to work briefly yesterday, but by the evening it would just load the video completely, freeze mozilla, and make me force quit the window. Amarok is acting similarly, it will open up fine but when I try to import, or even play a cd it freezes and has to be forced quit. Same thing with rhythm box and sound juicer, they open but as soon as I try and use them it freezes and has to be shut down. In fact, up until I booted up this morning it wouldn't even read when an audio cd was in the drive, but magically the icon appeared. I have no clue what is going on so any help would be appreciated.

---

### Post by Inxsible on 2007-08-23
That is strange !

Could you give us your system specs?

---

### Post by haruspex on 2007-08-23
I know its a 2 year old Dell dimension 2400, Celeron processor I beleive, 256 mb of ram.

---

### Post by Inxsible on 2007-08-23
> **haruspex said:**
> I know its a 2 year old Dell dimension 2400, Celeron processor I beleive, 256 mb of ram.
Ubuntu might run a bit slow with that memory although it is sufficient. Xubuntu might be a good bet or Damn Small Linux or Puppy Linux

---

### Post by frrobert on 2007-08-23
Just to rule out a memory problem, run the memory test that is on the Grub menu.  Run through all tests and make sure the memory is not bad.

---

### Post by asmoore82 on 2007-08-23
sounds like bad video RAM

---

### Post by rexy on 2007-08-23
well try booting into console mode, you can tell grub to do that, but i cant recall right now how. If booting into the console is stable you have to start digging elsewhere. maybe xorg.conf

---

### Post by Terl on 2007-08-23
> **haruspex said:**
> I know its a 2 year old Dell dimension 2400, Celeron processor I beleive, 256 mb of ram.

Sounds like my old pc.  If it is the stock Dell Dimension 2400 then it also has on-board video that shares some of that 256MB of ram.  You may want to look into Xubuntu as mentioned earlier.  It will free up resources for you.

---

### Post by asmoore82 on 2007-08-23
And just to make life harder ...

If your Motherboard is sharing RAM with Onboard video and you have a Bad spot in that shared area,
the Memtest won't be able to find it.

---

### Post by haruspex on 2007-08-23
I ran the memtest for 8 hrs while I was at work, when I rebooted it was at PASS: 53 Errors: 0. I also noticed that today websites with embeded media that worked perfectly fine yesterday (myspace music and  youtube mainly) cause firefox to freeze and crash today. Will adding more ram solve these problems? I know the dimension has an empty slot I could slip 512M in.

---

### Post by RJARRRPCGP on 2007-08-23
> **asmoore82 said:**
> sounds like bad video RAM

Disagree! 

Bad video RAM probably would cause the PC to have a POST failure or the BIOS screen is corrupted. 

With bad video cards, the BIOS usually would act like there's none or it boots, but even the BIOS display is corrupted.

Or else, it's fine in 2D, but when you use 3D, it crashes. If none-3D applications are simply ignoring you, it more likely is a driver issue or because the video hardware isn't supported. 

It should be fine if you get a Nvidia video card, at least a GeForce 4 MX PCI.

---

### Post by RJARRRPCGP on 2007-08-23
> **haruspex said:**
> I ran the memtest for 8 hrs while I was at work, when I rebooted it was at PASS: 53 Errors: 0. I also noticed that today websites with embeded media that worked perfectly fine yesterday (myspace music and  youtube mainly) cause firefox to freeze and crash today. Will adding more ram solve these problems? I know the dimension has an empty slot I could slip 512M in.


Your previous problems sounded like sound driver issues. I suggest that you pop in a SoundBlaster PCI.

---

