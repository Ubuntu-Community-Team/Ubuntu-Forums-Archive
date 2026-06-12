---
title: "Gutsy Upgrade HFS disk mount problems"
date: 2007-11-03
forum: Apple PPC Users
---

### Post by roeghar on 2007-11-03
Hello,
 I'm a new poster on the Ubuntu ppc forum but have been following it for over a year and have found it helpful in getting Ubuntu working on my G4 Digital Audio Mac. I started with Edgy, when ppcs were still officially supported, and upgraded to Feisty and now Gutsy. By and large it's been a fairly painless experience. 

Gutsy is working well except for one glitch that I didn't  have with Feisty-- mounting my hfs+ disks. I should mention that I have Ubuntu installed on a 10 meg SCSI hard drive with an Adaptec PCI card and two hfs+  IDE drives with OSX 10.3.9 and storage partitions. In Feisty I'd set up my mount points and manually mounted them in the terminal. Also at some point Disk Mounter began putting disk icons in the main title bar and all that was needed was to mouse click to mount them. They were basically read only, but I'd set permissions to allow me to access and copy files to my Ubuntu desktop. All was well until Gutsy. 

Now (most of the time--more on that later) it's as if the hfs disks don't exist on the system. Running fdisk -l in the terminal shows only the Ubuntu SCSI disk and a portible firewire disk if I have it connected; gParted the same. Until one morning I sat down at my computer to check BBC news and the local weather and, to my surprise, there were the disk icons strung out across the top of the screen. With a click and a password they mounted and I was back in business--that is until I restarted Ubuntu after booting into OSX to view a flash video I wanted to see on the StarTribune web site (Ya, gnash has its definite limits.) Now I'm back to no hfs disks. 

I guess I could wait a week or two and see if the some mysterious force working behind the scenes in Disk Mounter 2.20.0 suddenly manifiests  them again, but really I would like to know what's going on with this erratic behavior of Gutsy and get some ideas on how to fix it.

Oh, two other details: 1. My zip disks also no longer mount. 2. When I boot up the system using my Feisty CD, everything works just fine.

---

### Post by roeghar on 2007-11-03
OK, I know its not good form to respond to one's own posts. but a wierd solution just presented itself. Just for kicks I thought I'd check to see if my USB flash drive was also unmountable. When I inserted it in the usb port, it flashed a few times as usual and then as it mounted all the Disk Mounter Icons scrolled out in the top bar. They were all mountable and worked fine again. So the key for me seems to be to plug in the USB drive .Also, in the terminal all my disks show up using fdisk -l. Gutsy sure seems to have some strange bugs or should I say apes in it.

---

