---
title: "Multi OS Troubles"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Phase22 on 2007-10-07
Hi. I had Windows XP Home and a week ago I decided to get a 3rd hard drive (which was SATA) so I could put a Linux (Ubuntu) and a windows (XP x64 Pro) then my other 2 hard drives would be dedicated to just my other applications so if windows crashed (which it did a few weeks earlier) I wouldn't have to reformat a drive that has some applications on it that I would miss.

I now can't seem to install the OS's. We'll start with windows x64 Pro.

I install it (pick partition, go through formating and installations, ect) and then it prompts me to restart and when it restarts it SHOULD go to the next step in the installation process which should be more GUI based. Once I restart I take out the CD and go into BIOs to set it to boot from that hard drive. So it reboots after I make the changes and all I see is a blank screen with a cursor (white) in the top left blinking. It stays like that and I have no idea what to do next.


Linux (Ubuntu):

I put the disc in and install it. I get past the part where you go to the desktop and hit "install" then you pick your partitions. Before I go on i'd like to ask what partitions I should have for linux? I decided to just format my other HD because I haven't installed anything special on there since I had to reformat a week ago due to a windows crash. I put XP on there and like I said above it doesn't finish the installation.

My first partition:
Primary (Primary or Logical)
30gig (out of 80 gig)
Beginning (Beginning or end)
Ext3 (ext3, fat32, ect)
mount point = /

My 2nd Partition:
Primary
2 gig
beginning
swap
mount point = I left that blank

After I make the partitions I install, after the isntallation it prompts me to restart and says I can restart or I can continue to run off of the CD but if I change anything it won't save. I then restart and take the CD out and go into my BIOs and boot from the HD. Once I change the bios it boots and gives me a screen that says something like this:
"Grub Loader step1.5

Grub is loading, please wait...
Error x"

x= 15, x = 16, or x = 17. It varies.


With both OS's I sometime get messages that say
"Error loading Operating Systems" or that blank cursor.

---

### Post by cameronw on 2007-10-09
Hi there,
I wasn't quite clear if both operating systems are to be installed on the same hard drive or not. If so I am pretty sure Windows will only boot if it's at the beginning of the hard drive (not sure why but make sure it's on the first partition). The blinking cursor probably means it cannot find anything to boot from as I've experienced that before when the hard drive was accidentally reformatted. Where have you installed the bootloader (GRUB) by the way? hd0 (the MBR) or hd0,0 (1st partition) or somewhere else. If you don't know where this is it's in the advanced box right before it installs it - the default is hd0 I believe. As for the error codes I'll have a look around for what they mean and when you get back to me I might know what's going on. By the way your Ubuntu partition setup seems to be OK.

---

