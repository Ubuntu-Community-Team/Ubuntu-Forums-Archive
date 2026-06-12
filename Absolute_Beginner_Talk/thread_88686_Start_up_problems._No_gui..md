---
title: "Start up problems. No gui."
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by Dave Hook on 2005-11-10
Hi all, i have downloaded and installed the UBUNTU iso file, for some reason after being installed i am not getting the window interface (GUI i think). Have i downloaded the server version of it. The file i downloaded is ubuntu-5.10-install-amd64.iso. If not any ideas to solve the problem. When the system starts i get dave@ubuntu:~$ then i struggle from there to work out what to do.
I have tried to search the beginer talk with no joy.
Dave

---

### Post by 23meg on 2005-11-10
There isn't a separate server version of Ubuntu. What processor do you have? The version of Ubuntu you've downloaded is for the AMD64 family of processors.

---

### Post by gord on 2005-11-10
when you first booted up with the ubuntu cd in the drive (pre install), it came up with a small splash screen. did you just press enter or type 'server'?

---

### Post by ausm on 2005-11-10
[QUOTE=gord]when you first booted up with the ubuntu cd in the drive (pre install), it came up with a small splash screen. did you just press enter or type 'server'?[/QUOTE]

I am having the same problem. I am running the 64 bit version of Ubuntu and i was setting up a dual boot. 

Here is what I did and what is happening

Please keep in mind these Operating systems are on two seperate drives.

I also ran Ubuntu on a live CD and it worked great.

1)Loaded Win Xp on the slave drive 120 gig just for gaming no problem

2)I attempted to install ubuntu desktop version and it completely went through the installation but hung up every time it was installing GRUB. I tried it three times no luck.

3)I tried loading the server version and it work flawlessly(recognized my Win XP installation) except for it puts you in terminal mode and no GUI?? How do i get the GUI back up and also how can I edit the grub so it will not do this again?

TIA,

Ausm

---

### Post by Kapre on 2005-11-10
[QUOTE=ausm]I am having the same problem. I am running the 64 bit version of Ubuntu and i was setting up a dual boot. 

Here is what I did and what is happening

Please keep in mind these Operating systems are on two seperate drives.

I also ran Ubuntu on a live CD and it worked great.

1)Loaded Win Xp on the slave drive 120 gig just for gaming no problem

2)I attempted to install ubuntu desktop version and it completely went through the installation but hung up every time it was installing GRUB. I tried it three times no luck.

3)I tried loading the server version and it work flawlessly(recognized my Win XP installation) except for it puts you in terminal mode and no GUI?? How do i get the GUI back up and also how can I edit the grub so it will not do this again?

TIA,

Ausm[/QUOTE]


Ausm - once your on the terminal mode, pop in the cd and then type "sudo apt-get install gnome-desktop".

K

---

### Post by ausm on 2005-11-10
[QUOTE=Kapre]Ausm - once your on the terminal mode, pop in the cd and then type "sudo apt-get install gnome-desktop".

K[/QUOTE]

Thx Kapre! I just did a search and found some more documentation on it here.

[http://www.ubuntuforums.org/showthread.php?t=81258&highlight=Installation+server+GUI](http://www.ubuntuforums.org/showthread.php?t=81258&highlight=Installation+server+GUI)


I did'nt realize that the server install is just the bare minimum.

Ausm

---

