---
title: "Good Backup Program"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by CharlieRC on 2007-04-27
I am new to the Linux world and just installed Ubuntu 7.04. I would like to back up the OS before I get creative and screw things up. Can someone suggest a good backup program to use?

---

### Post by psusi on 2007-04-27
man tar

Assuming you have ubuntu installed on one partition ( not a separate /home partition ), this will backup your whole system to a file named backup.tar.gz in your root directory:


sudo tar czf /backup.tar.gz --exclude=/backup.tar.gz -l /

To restore:

cd /
sudo tar xzf backup.tar.gz

---

### Post by CharlieRC on 2007-04-27
Thanks for the suggestion. It just finished running. But what if you can't even boot the OS? Is there a Linux program like Ghost or Acronis in the Windows world?

---

### Post by psusi on 2007-04-27
You can boot from the livecd, mount the hard disk, and restore that way.  Usually though you can at least boot the system in rescue mode even when it is hosed up, and you should do that when restoring anyhow.

Also the partimage package is kind of like ghost.

---

### Post by TheDoulos on 2007-04-28
I've been using [PartImage]("http://www.partimage.org/Main_Page") which is contained on the [System Rescue CD]("http://www.sysresccd.org/Main_Page") Live-Boot CD.

---

### Post by Bachstelze on 2007-04-28
[http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage)

---

### Post by glerg on 2007-04-29
> **CharlieRC said:**
> Thanks for the suggestion. It just finished running. But what if you can't even boot the OS? Is there a Linux program like Ghost or Acronis in the Windows world?

Yes, Acronis works fine.  Just make sure you use it with the "rescue"CD and it will perform for you.  I have used the Acronis rescue boot CD several times to backup my installation and to restore a couple of installations.  Takes less than 15 minutes on my Thinkpad R51 laptop.

---

