---
title: "Help with 6.10 Amd64 install or removal"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by shooter902 on 2007-02-20
HI Guys, Really a newbie here! But willing to learn, I will try to explain myself as best I can, If I leave anything out I know you will ask :) 

I'm having trouble with the DVD install of 6.10 AMD64. I am running an AMD X2 4400 on A DFI CFX3200 MB, 2 gig of ram, ATI X1600 Video card, 4 SATA drives (C,D,E,F)

My "D" drive is 160G in size with about 50G of data that I wanted to save. I backed it up and started my install.

Rebooted the system and set the boot drive to my second or "D" in the BIOS. I set the BIOS to boot from CD and off I went. The system booted into the live CD interface and I clicked to do the install.

I walked through the install with no problems. I chose my "D" drive (WD1600) to install to and told it to use 50% of the drive (want to keep the NTFS partition with my data on it even though I had it backup up) and all appeared to go well.

The Install finished and told me to restart the system, I clicked restart and it ejected the DVD and ask me to close the tray and hit enter, I did so and waited for days (actually 45 mins) with a solid HD light. I did a reset and when the system tried to boot the drive with the new install it told me there was an error with the operating system and stalled.

I then figured that I must have interupted the install somehow and did another install, this time telling it to take the whole drive and format it. Again, all went well until I went to reboot and it hung at the same place (at the restart close the tray and pray screen) again I did a reset and got the same OS error message..hmmmm..

What am I missing here? Of course I can no longer see my "D" drive in XP anymore. I would be happy either to find out why the install is failing OR If someone could tell me how to delete the partitions (in simple terms) so I can have my drive back in Windows and install Ubuntu on a second AMD 3800 system I just built from spare parts.

Sorry if this is too wordy, didn't want to leave anything out..but I know I did :KS 

Thanks a ton for any help..

Phil

---

### Post by dwblas on 2007-02-20
Did you get the initial grub screen where it asks you which os you want to boot?  Also, post the error itself.

---

### Post by shooter902 on 2007-02-20
Hey DWBLAS, Nope, I didn't get the GRUB screen. However, just a note, It is the only OS on the drive (not a duel boot) and I'm telling my BIOS to boot from the drive with Ubuntu.

The Error I get just says: "Error loading operating system" and stops there.

Thanks

---

### Post by dwblas on 2007-02-20
Grub can't find the os. 
Excuse me.  You can do all of the following, but I just remembered that you can call grub from the command line.  When the boot hangs, you either key in "grub" with no --config-file, and then the rest of the stuff at the end of this post, or you are already in grub so it will say something like error-not a grub command, and so key in everything else until it boots.  If that fails, then fall back to the following.  If it succeeds, you still have to reinstall grub according to the following, except forget the "-- config-file", etc. as grub now knows where it is.
Original Post:
I have used Knoppix since before there were live CDs, so I don't know what it takes to boot from the live CD, but once you have a linux system running you want to reconfigure grub.  First mount /dev/hdb2 if that is where Ubuntu is.  Look in /boot for vmlinuz-Blah which is the kernel.  You should also have a /boot/grub dir which will have the menu.lst file in it.  If all is as it should be invoke grub and do as follows:
assuming /dev/hdb2 contains Ubuntu and is mounted at /media/hdb2 (you aren't using SATA, I hope)
grub --config-file /media/hdb2/boot/grub/menu.lst
root (hd1, 0)              ## /boot is on 2nd disk drive (hd1) and is the first partition (0)
setup (hd0)               ## write to MBR
quit

---

### Post by shooter902 on 2007-02-21
OMG.. Thanx Dwblas for the help but none of those fixes apply to me? I don't think?? I'm a totally newbie and that looked and sounded to complex for me. 

Yes I am using SATA drives..maybe I should do more research or just forget the whole thing.

Thanks for your help :)

---

### Post by dwblas on 2007-02-22
I had the same problem with AMD64 Feisty KUbuntu, but not with XUbuntu 32 bit.  I'm thinking that this is unique to 64 bit installs for some reason.  If this is your first install, try out a 32 bit version.  It should install cleanly.

---

