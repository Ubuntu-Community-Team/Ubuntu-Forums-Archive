---
title: "Ubuntu 6.06 won't recognize SATA"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by r01sa on 2008-05-19
Hello!

To preface, I am a newcomer to the Ubuntu scene, so forgive the newbie questions/knowledge that I will more than likely present throughout. :)

Ok, I have a Blue and White G3 with Ubuntu Server 6.06 installed.  I have a SATA PCI card installed in the machine, with a 500 GB drive attached.  The OS is installed on a 6GB IDE drive.  The install goes off without a hitch.  It even recognizes the 500 GB drive at that point.  But after the installation, I cannot get it to find the drive.  An fdisk -l presents the IDE drive, but not the SATA drive.  I tried to enter in the information in /etc/fstab, but upon a reboot nothing seems to happen.  Reading the logs didn't seem to really provide anything, although I have to admit the logs had a lot to say, I just may not have the knowledge to comprehend.  Any advice you can give would be appreciated.  Thanks in advance!

---

### Post by stream303 on 2008-05-19
Looks like you'll want to use

mac-fdisk

to partition that extra drive, and then mount it manually, or put it into /etc/fstab.

I don't have any personal experience with mac-fdisk, so hopefully someone can jump in.

I did see some good info on the Gentoo wiki:
[http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=4#doc_chap3](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=4#doc_chap3)

that might help out, although the focus is on a boot setup.

---

### Post by r01sa on 2008-05-20
Hmm... I'll give that a shot this evening.  Thank you!

---

