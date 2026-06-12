---
title: "PCMCIA install issues"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by Brigrat on 2006-01-29
Not sure if I need to put this here in absolute beginner or Laptops.  So I’ll do both as the question might help someone else with a desktop later.

I have a Compaq Presario 1270 laptop, (intell 433 with 128ram) old but durable, running breezy 5.10.  Since it does not have onboard network I need to use a PCMCIA card.  I used a D-Link DFE-670txd card before with windows and it worked fine.  That card is no longer supported and never had any known LINUX drivers.  I bought a DYNEX DX-E201 card that does have linux drivers.  I then installed the new card it was not seen by the system.  It still shows the old card.  I was using this machine to play with the different distros to see which I wanted to use, so with nothing on it except the OS, I just wiped the drive and re-loaded.  On the install I had the card installed but is did not appear to be recognized at all.  The card works as it was tested on a separate machine, under windows. The cd has three files on it for LINUX.  That are the driver files, but again Idon’t know what to do with them.  I have been lucky so far as everything else has installed and ran. The files are:
copying .txt          which is about the licensing.  Dxe201.c  looks like it might be driver
                             info based on the comments to realtek components. 

kern_compat.h  (kern_compat.h: Linux PCI network adapter backward compatibility code. */)  No idea here.  

Last on e is called makefile.  Below is the infor from that file

# Makefile for a basic kernel module

LINUX=/usr/src/linux
CC=gcc
MODCFLAGS := -DMODULE -Wall -Wstrict-prototypes -O6 -I$(LINUX)/include

dxe201.o:	dxe201.c
		$(CC) $(MODCFLAGS) -c dxe201.c

	This looks like part of the install info but not sure how to run with this one.

Here are my questions are:
A.	How do you remove old hardware devices to ensure that there are no conflicts?
B.	How do you install new hardware the is apparently in my case not PnP compatable. ie install/update drivers.

I have googled and searched the forum for basic info on installing hardware and could locate anything.  Is there a basic tutorial on how to replace hardware/ install new etc that includes driver install how to’s


Thanks for any and all help here.

Dan

---

