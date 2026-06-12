---
title: "Adding a driver during install"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by nzcyclone on 2007-06-17
Hiya, Hopefully this is the correct forum to ask this, have asked similar but I think posted it in wrong area and under someone elses problem and it wont let me delete it, sorry.

Am trying to install Ubuntu 7.04 on a Semprom 3000+ with 1gb ram. The HDD trying to install on is a ATA but is not off a IDE port instead is on a SATA / ATA card. With having a read on here I went and got a program called GParted with that I get to the main screen with a window open but it is showing no devices. I do have a linux driver for the card. When trying to install Ubuntu it gets to the partitioner and just wont get past that I get a I/O Error with options of retry / ignore / cancel if go ignore it then waits a while and gives me a windows titled "Partitions formatting" showing 33% and just sits there. is there  a way to tell the installer to load this driver or am I goosed? This computer was running Windows Server fine but so want to get away from that but if cannot get this installed will have to go back to it. Any help greatly appreciated, thank you :)

---

### Post by nzcyclone on 2007-06-18
Doesnt matter have taken it back to Windows 2000 Server.

---

### Post by nzcyclone on 2007-06-18
Decided wasnt giving up that easily. I have now at least got the GUI up of Ubuntu Desktop

went into device manager and yes it is detecting the card and everything fine in there. and best part is GParted too is now seeing it and is saying disk space is unallocated. When try to allocate it it is saying needs to "Set Disklabel on /dev/sda" when go create and create again it is saying "Error while setting new disklabel" 

What does this error mean?, well know what it means but what do I do to fix it so do not get that error and it allows it to format and create a new partition?

---

