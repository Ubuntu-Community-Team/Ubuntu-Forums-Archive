---
title: "newbie install of 5.10, ati, dualview, sata, pata, grub"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by mediaservant on 2006-02-01
Ok this post is for all the other newbies out there, to help spread a LITTLE knowledge.

First of all, I’m not a total linux newbie, I have installed redhat 5.10, mandrake 9, 10, etc, but never installed a distro that had everything I wanted, etc. I always go back to windows real quick.

I have:

AthlonXP 2500
ATI Radeon 9600 AGP dual head
Nforce2 motherboard
SATA 37gig 10kRPM
PATA 120 gig

This time, I was very determined to switch from windows completely.  Here is a list of my steps:  (1,2,3 etc are main steps, a,b,c are sub-steps or additional info)

1)	research.  I found that ubuntu was the best distro, followed by (IMO) mepis.
2)	More reseach.  I required the following things to WORK:

a.	ATI dualview for video editing
b.	Firewire
c.	Easy install of non-typical apps such as cinelerra
d.	DV video capture

3)	Get the live CD’s – ubuntu, kubuntu, mepis
       
         a. ubuntu community is the BEST

4)	Test out live cds on multiple computers and install ubuntu on a test system

a.	Firewire works
b.	Usb works
c.	Installation of anything and everything is easy
d.      Vid cap works

5)	Boot to ubuntu, partition for dual boot and install
6)	Ubuntu installed, but “failed to load operating system” on boot

a.	I installed to a SATA, and have a PATA drive for data.
b.	Grub was installed incorrectly

7)	Give up on dual boot, Reinstall ubuntu, boot to mepis cd, mess with grub
8-	Mess with grub a lot, finally install mepis to see if it works

a.	Mepis installs

9)	Boot to grub with gui, which sends me to another grub and dead ends

a.	Mess with mepis and grub some more

10)	Do what I should have done first – DISCONNECT THE PATA

a.	I’ve seen comments that it’s best to install grub to a SATA with no PATA drives installed if you aren’t using the PATA for booting

11)	Install MEPIS and it works

a.	Dumb, I was setting out to use UBUNTU

12)	Reconnect PATA and it still works
13)	Try to get fglrx and dualview working
14)	Pound my head against the wall with editing config files
15)	Pound my head against the wall with x server crashes
16)	Remove nvidia drivers (??!!??) and try to get the ALSO INSTALLED ati drivers working
17)	Give up on MEPIS and install ubuntu

a.	I’d already found wiki’s and howto’s for installing ATI drivers on UBUNTU
b.	Ubuntu was what I wanted to use anyway, had an uneasy feeling about mepis
c.      mepis has a VERY GOOD Live CD

18-	Disconnect PATA and install UBUNTU
19)	It works
20)	Follow steps in ubuntu wiki about installing ATI drivers
21)	Install ubuntu standard fglrx
22)	No ATI setup interface found
23)	Decided to NOT edit another x config file ever again
24)	Install ATI provided binary drivers per instructions found in wiki

a.	Installed from the repository, not really from ati

25)	ATI config interface found, but dualview select does not stick
26)	Give in and run fglrxconfig - one last time

a.	Yes, the driver is there but xorg.conf is apparently the same??

27)	Once you install the latest ATI binary drivers from the special repository, the fglrxconfig is NEW and apparently WORKS.

a.       Saw an old tip about using fglrx to generate the good SECTIONS of xorg.conf to paste into your original, NON CRASHING xorg.conf
b.       Did not do that.

28-	Restart x server (ctrl-alt-backspace)
29)	Adjust desktop resolution to twice the width and same height
30)	Enjoy dualview.

a.       Praise God

31)	Follow steps for installing cinelerra

a.	Alien is required because cinelerra is provided with RPM

This took me from 8:30 pm to 2:00 AM.  Painful, but it's done and now I know how.  Now you do too.

---

