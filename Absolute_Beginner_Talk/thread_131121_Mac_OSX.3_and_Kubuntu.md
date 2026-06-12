---
title: "Mac OSX.3 and Kubuntu"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Derktoon on 2006-02-15
hey there, im attempting to install Kubuntu on a drive that will dual boot OSX.3...what is the process for that and is there anything i should know beforehand (IE "you'll need to hold down such and such key when your booting")

---

### Post by Protostar on 2006-02-15
I have a Mac (but haven't used it for a while) and as I remember you have to hold down the "C" key when the computer is starting up to boot from a CD/DVD. Other than that, I don't know anything about installing Linux on a Mac.

---

### Post by linear on 2006-02-15
Required reading:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

What worked for me (Ubuntu, not Kubuntu, but in principle the same):

0. Read up in the PPC forums (more traffic in the Ubuntu than the Kubuntu) on any model specific quirks.
1. Back up OS X partition. (Carbon Copy Cloner works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using parted to resize non-destructively.
3. Boot from the Kubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

Good luck!

---

