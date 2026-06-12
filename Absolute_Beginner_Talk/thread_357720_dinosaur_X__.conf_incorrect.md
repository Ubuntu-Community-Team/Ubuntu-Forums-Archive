---
title: "dinosaur X  .conf incorrect"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by treaderll on 2007-02-10
Target motherboard: 1995 Intel Marl with 80meg ram, 1.7Gig hda(swap), & 250Gig hdb, 21 scsi cdroms
Unable to install Xubuntu 6.10 using the target 1995 Intel motherboard, I moved the hard drives
I wanted the OS on to another mobo which has a built-in videocard.   Of course, Xubuntu found that videocard, and not the Cirrus 5424 that the monitor is actually plugged into.   So X complained that I must edit the configuration file before restarting GDM (lack of clue about GDM!) TLDP says the name of the driver is cirrus.  
On restart, machine halts before arriving at login.
Can I tell grub to start the os single-user command line?  If so, how?
Do I just replace cyberblade whatever with cirrus in /etc/X11/xorg.conf, or is there more I must do?
If you are aware of documentation either on-line or hard copy for the following I would greatly appreciate it:
1.configuring X,
2.starting gdm,
Off topic... 
3.writing a /etc/fstab that is less silly than the one Xubuntu congered, or maybe writing a udev  .conf to do the same.  What I have in mind is cd1 is the first tray of the first cdrom drive of the first adapter, increasing by trays, then drives, then adapters, rather than the randomness
I am now faced with.  I found some things on the subjects online, but they did not help with my aim.

Thanks in advance, 
treaderll

---

