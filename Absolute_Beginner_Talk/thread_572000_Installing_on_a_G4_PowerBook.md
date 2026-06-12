---
title: "Installing on a G4 PowerBook"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by brandonlouis on 2007-10-09
Hi.  Has anyone written a good tutorial on installing  the latest stable release that supports the G4 PPC. I have never used any linux distro, but I have learned to use the terminal fairly comfortably in OSX. I would like to be able to dual boot (can I create a seperate partition without wiping my own? I don't have a firewire drive to create a bootable back-up, I do have a USB drive, though)  with Tiger and I hope to get the Airport Extreme working, if that is possible. I tried searching for a guide to do these things, but I am not sure what version of ubuntu I need, and nothing was clear enough for a totally new user to get.

Thanks in advance.

---

### Post by Incense on 2007-10-09
You'll find the install CD at this link

[https://wiki.ubuntu.com/PowerPCDownloads]("https://wiki.ubuntu.com/PowerPCDownloads")

As far as installing, the least painful way is to reinstall OSX, and set aside a partition for ubuntu before you install OSX. Then run the live CD, and tell the partitioner to use the largest amount of free space, and it will set up your special PPC partitions for you. (You need a special bootstrap partition). I'll see if I can find a link for you. Be advised that you have no flash support, only Gnash, and some packages are not made for the PPC (Mostly Wine apps) but you can run MOL (Mac On Linux) to access OSX from Linux. That's kind of cool.

---

### Post by Incense on 2007-10-09
I found this for you.

[https://help.ubuntu.com/community/Installation/PowerPC]("https://help.ubuntu.com/community/Installation/PowerPC")

I talks about installed 5.10, which should be the same process if you download the alt installer from that other link I gave ya.

---

