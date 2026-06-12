---
title: "Hi guys, need help!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by derricpeterson on 2007-12-27
I have a question about Ubuntu. My friends told me that I can run several OS with Ubuntu. Is it right?
Can I run for example Ubuntu and Windows at a time? Need advice.

---

### Post by ericmc783 on 2007-12-27
yes, you can set up a dual boot.

---

### Post by derricpeterson on 2007-12-27
Is it difficult?

---

### Post by rickycodie on 2007-12-27
no just install windows first and then ubuntu.

---

### Post by jas0 on 2007-12-27
ericmc783 is right. It is indeed fairly simple to set this up. The best idea is to leave your Windows partition in place and plug in an extra hard drive for Ubuntu. When you boot into Ubuntu using the live CD, just select Ubuntu to be installed on the newly added hard drive.  This should be all you need to do.

If you do not have an additional hard drive, you can still dual boot, but the process is a bit more involved.

---

### Post by derricpeterson on 2007-12-27
Can't it break both systems Windows and Ubuntu?

---

### Post by derricpeterson on 2007-12-27
Ok thanks, I'll try it! :)

---

### Post by xeth_delta on 2007-12-27
> **derricpeterson said:**
> I have a question about Ubuntu. My friends told me that I can run several OS with Ubuntu. Is it right?
Can I run for example Ubuntu and Windows at a time? Need advice.

If what you meant is run Windows or some other OS from inside Ubuntu, simultaneously, you could use VirtualBox / virtualization. There are a lot of threads about it on the forum where you will be able to find information.

Good luck!
Xeth

---

### Post by jas0 on 2007-12-27
> **derricpeterson said:**
> Can't it break both systems Windows and Ubuntu?

Yes, it is possible. You'll be modifying fundamental things in your system configuration. Thing may go wrong. Heck, this is partly what this forum is for :-)

Always back up your data before attempting to install Ubuntu. While most of the time you will be able to get it back from a botched install, you never want to risk it.

---

### Post by tachyon4 on 2007-12-27
I'm completely new to all of this, so details would be appreciated.

I have Windows Vista now and I want to install Ubuntu.  How do I double boot without an additional hard drive?  How do I partition my hard drive?

Thank You.

---

### Post by jas0 on 2007-12-27
> **tachyon4 said:**
> I'm completely new to all of this, so details would be appreciated.

I have Windows Vista now and I want to install Ubuntu.  How do I double boot without an additional hard drive?  How do I partition my hard drive?

Thank You.

First of all, right click Computer in Vista and select Manage. Expand the Storage section and click on Disk Management.

Tell us what you see.

---

### Post by tachyon4 on 2007-12-27
I've got DATA (D:), HP_RECOVERY (E:), and OS (C:).

C and E are on Disk 0 and D is on Disk 1.

---

### Post by Martin Witte on 2007-12-27
it depends a little how your disk is partioned currently. if you have two or more partitions on one disk in vista (you will see at least  a c: and a  d: in windows explorer) you can move all data from eg. the d: partition to the c: (provided it is at least 2GB (see [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) for the system requirements, i guess a vista user meets them easily). see eg. this guide then [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) on how to install. if you have one partition you can resize the ntfs partition (provided you have empty space in it), but i consider that as an advanced subject - see eg. [http://nishants.net/articles/ntfsresize.htm](http://nishants.net/articles/ntfsresize.htm)

---

