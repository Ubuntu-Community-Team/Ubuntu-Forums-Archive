---
title: "Just getting started"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by happymonkey on 2007-03-19
I am trying to get Ubuntu to work on my computer but have so far had little luck. I am running into a few issues and was hoping that someone here may have some information that I can use to get it running.

The computer is a Dell Dimension with an ATI graphics card. This means that Ubuntu throws a number of display errors when I try to launch it from CD. I have read in a few places how to change the configuration files so that it will work with my ATI card, but since I was running off of a CD, the changes I made would not save.

I decided to use the Ubuntu windows setup tool but have run into issues there because of the way that Dell set up the hard drive in my computer. The drive already has four partitions on it and they are not set up in a way that the Ubuntu installer can work with.

I purchased an external firewire drive to attempt to install Ubuntu there. I was able to start Knoppix and run gparted to create a primary partition for linux and a linux-swap partition. I then ran through the instructions on [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix) and was able to get the Ubuntu files downloaded and got to the part of the document where grub is set up. This has not worked and I am not able to figure out how to set up a duel boot environment so that I can get my computer to boot into Ubuntu on the firewire drive that is hooked up to the computer. Is what I am trying to do possible? And if it is, what other steps should I take to get this done?

---

### Post by Icemanyurt on 2007-03-19
Are you trying to keep windows on the machine as well?

If not, I would format the drive and start again (or let the partition tool erase drive and setup how it wants to go)

---

### Post by Moeru on 2007-03-19
What version are you using? I had the same problems with an earlier version of Ubuntu. I'm running 6.10 right now and it runs awesome on my PC. ATI will be a headache due to ATI's lack of support for Linux drivers but you should be just fine after some help.

---

### Post by happymonkey on 2007-03-19
I do want to keep windows on the system as I have other family members who use the computer (wife and kids) and they will want to make sure that the interface they are used to and the software they use are intact. That's why I haven't wiped the drive clean. 

I am trying to run 6.10 but can't get the visual interface to work. I get the typical X windows error that I have seen reported on so many different forums about the ATI card.

Any more questions that I can clear up?

---

### Post by Moeru on 2007-03-19
If you can take the format, do so and repartition Windows into its own nice little section, leaving the rest behind for Ubuntu. There's a few Dualboot HOWTOs on the forum and a ton on the net for exactly how to do the install step by step

---

