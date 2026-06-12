---
title: "Installing Ubuntu with windows"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by pauld76 on 2007-04-12
I am planning to install ubuntu on my windows xp machine. It is my first foray into linux so I obviously want to keep windows xp in case. I have a single 80 gig harddrive. My question is can I have windows and ubuntu on the same harddrive and switch beteen the 2 at boot up? If so how do I do this?

I have quite limited knowledge of harddrives and partinioning etc. Any help would be greatly appreciated.

---

### Post by CJay554 on 2007-04-12
simple process called Dualbooting
sadly i have no time to assist at the manner right now...
but you can google dualbooting... or wait for someoen to respond :/
it just mainly deals with splitting a partition into 2 kinda bad if u have windows saved on you 80 gig all the way,
you would want to have free space of at least 10 gigs to partition a segment for ubuntu
all the partitioning is done durring the installation,
which you would begin by starting your computer with the ubuntu CD in your CD drive, and on

---

### Post by pauld76 on 2007-04-12
> **CJay554 said:**
> simple process called Dualbooting
sadly i have no time to assist at the manner right now...
but you can google dualbooting... or wait for someoen to respond :/
it just mainly deals with splitting a partition into 2 kinda bad if u have windows saved on you 80 gig all the way,
you would want to have free space of at least 10 gigs to partition a segment for ubuntu
all the partitioning is done durring the installation,
which you would begin by starting your computer with the ubuntu CD in your CD drive, and on

Thanks for quick response.  Ive actually got 60 gig free so theres not a problem there.  Ill google it and see what it says.

---

### Post by thefoolisme on 2007-04-12
If you do a search for dual-booting on this site, you'll come up with tons of responses with links.  Here's a good place to start reading:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Basically, you would use gparted on the install disk to resize the Windows, and create the new partition.  

Word of advice:  defrag Windows at least 2x before resizing to make sure it's ready to go, or else you could have problems with the resize.

---

### Post by pauld76 on 2007-04-12
> **thefoolisme said:**
> If you do a search for dual-booting on this site, you'll come up with tons of responses with links.  Here's a good place to start reading:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Basically, you would use gparted on the install disk to resize the Windows, and create the new partition.  

Word of advice:  defrag Windows at least 2x before resizing to make sure it's ready to go, or else you could have problems with the resize.

Thanks for the link.  Theres a good tutorial there with screenchots,  It looks idiot proof.  Im just defragging now while the iso finishes downlading.

---

### Post by sailor2001 on 2007-04-12
[http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu&hl=en](http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu&hl=en)   a graffical description of dual booting

---

### Post by pauld76 on 2007-04-12
> **sailor2001 said:**
> [http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu&hl=en](http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu&hl=en)   a graffical description of dual booting

Good video.  Im ready to go.

---

### Post by sailor2001 on 2007-04-12
to select which os you want to boot into, at loading it will show first ubuntu (0) ubuntu safe (1) memtest (2) xp safe (3) and xp (4) or something like that..... count to the os you want to start at boot up and then in terminal sudo gedit /boot/grub/menu.lst  and in the 1st para change the default to that specific number

---

### Post by gerrymoth on 2007-04-12
I've just set my 60GB laptop as a WinXP/Ubuntu dual boot system in the last few weeks.
1. Defrag your HD in Windows a few times. 
2. Download the ISO file from [www.ubuntu.com](www.ubuntu.com) and put on a CD (I started with edgy 6.10).
3. Put the disc in CD drive and reboot.
4. Select to install Ubuntu and follow the instructions to keep existing partitions and install in freespace. Think I reduced the size of my Windows partitioning to 30GB which created free space and installed Ubuntu with no problems.

I'd recommend reading the guides on Ubuntu website, the howto's on ubuntuforums and the excellent guides on [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) that's where I started and it helped understand what's going on.

---

### Post by Frank Golden on 2007-04-12
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

The definitive dual boot site.

---

