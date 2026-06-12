---
title: "ATI graphics card 3D effects started off fine, then deteriorated"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by happycamper on 2007-04-06
System: 1.8 GHz Pentium III, ATI "All-In-Wonder" Radeon 9600 graphics card, 800 Mb RAM, dual-boot with Windoze XP, but Ubuntu has its own HDD with about 50 Gb free space (ext3 file structure).

I installed 6.06 ~3 weeks ago, following the instructions for the ATI graphics driver, and at first it ran great. But gradually 3-D screensavers like Skyrocket, MatrixView and Flock began to run very slowly, so I began to suspect a problem with the graphics card interface. For example, the Flock screensaver shows a variety of complex, abstract 3D shapes that flow and spin across the monitor.  This used to work seamlessly and in a fluid manner, but now it's very jerky and freezes when the number of lines and forms gets too complex.

I read in a forum here that the speed at which glxgears runs is a good measure of a card's 3-D acceleration capabilities, but when I ran that in a mid-sized window the gears turned normally for ~ 1 second and then slowed to a jerky crawl. 

The same card works perfectly under MS XP on heavily graphical games like Star Wars Battlefront III, so I doubt there is anything wrong with the card itself. 

TIA for the help.

---

### Post by wpshooter on 2007-04-06
You did mean PIII, correct ?  If so, probably not a computer to be running XP and possibly Ubuntu at a reasonable clip.

When you installed Ubuntu did you setup a SWAP partition and if so, how much drive space did you allocate to it ?

And also, actually I am not sure that you needed to alter the O/S installed drivers for your video card !!!

---

### Post by ajgreeny on 2007-04-06
Try changing back to the open source ati graphics driver.  I use it with my ati 9200SE card and it works great.  OK, I'm not a gamer, but in glxgears it gives me figures of about 1200-1300fps when the gears window is on top, and about 8500fps when the terminal is on top the gears window, more than anough for me.

---

### Post by happycamper on 2007-04-07
First, thanks to both of you for the help.  wpshooter, I had to go back into Windows to check and I was wrong - the system is a 1.8 GHz Pentium 4, not 3, with 770 MB of RAM. It runs fime with some pretty intensive games like Star Wars Battlefront and Halo, so no complaints with graphics performance under Windows. As to partitioning, when I installed Ubuntu I left the 80 GB C drive to the Windows XP O/S and its NTFS file system, partitioned the D drive and gave Ubuntu 40 GB, which it now show as three partitions, 37 GB main, 1.5GB swap and another 1.5GB it uses for some arcane purpose.  Is there a specific way to check to be sure I did all of the partitioning right?

algreeny, I installed Ubuntu following the instructions in Keir Thomas's *Beginning Ubuntu Linux*, which seems pretty comprehensive.  That instructed me to install an ATI driver called fglrx using Synaptic (I also tried **sudo apt-get install xorg-driver-fglrx** from the command line and was told that nothing new needed to be installed), but I wasn't subsequently able to run either fglrxconfig or fireflcontrolpanel ("No such command or file") so I wonder if the installation took hold.  Is that what you mean by the open source ATI driver?  And if so, since I apparently have screwed up its installation, what next?  I am not adverse to a completely clean reinstallation of Ubuntu if that's what it takes, but I'm trying to learn how to work with this thing, and can hardly start from scratch every time I encounter a problem.

Not sure if this is relevant, but before the GUI appears after boot I get a black screen with the words "Analog Input:  Cannot Display This Video Mode" for ten seconds.  Even if this is meaningless, I would like to know how to get rid of it.

Finally, in general, how do I go back and check to see what went wrong with the installation of a program like fglrx?  And how do you count fps in glxgears?

Again, TIA for the help, folks.

---

### Post by ajgreeny on 2007-04-07
You will notice if you do a search on fglrx, that many, many people have had problems getting the driver to install and work OK.  The ati driver that ubuntu installs by default is quite good enough for most people and I would suggest you give it a try, as I said in my first post.

---

### Post by happycamper on 2007-04-08
I uninstalled fglrx per your suggestion, which (I presume) left the OS running with the default ATI driver, and you were right:  glxgears now moves properly.  I will be seeing if other 3D effects such as the complex screensavers are improved as well.  Thank you for your guidance.

As an aside, I am also a believer in the power of the pocketbook, and so I will be writing ATI/AMD to tell them that as a long-time customer of their pricey video boards, I will not be buying another one unless they make a credible attempt at Linux support.

---

