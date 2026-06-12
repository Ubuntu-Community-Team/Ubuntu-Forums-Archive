---
title: "Is there a way to install  over a previous version without exploding my dual boot?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by iteyoidar on 2006-11-10
I currently have version 5.10 of kubuntu installed, apparently, so I don't think the normal update thing is going to work.  There is that picture walkthrough of the installation from the live CD on here, but it isn't very clear about this.

Like if I try to install Ubuntu 6.10(or whatever the newest one is) from the CD, what do I do to make sure it doesn't try to reformat my hard drive or install over my Windows partition?  Thanks.

---

### Post by jpkotta on 2006-11-10
You want to do a dist-upgrade, not a reinstall. This will not touch your Windows partition (or any partition for that matter, it will only update files).

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Velotix on 2006-11-10
You have the option of upgrading by proxy; upgrading Kubuntu to version 6.06 and then to 6.10 immediately afterwards will work. Make sure you install **Kubuntu** and not Ubuntu unless you want to get used to a new desktop environment at the same time (Kubuntu uses KDE for the desktop, Ubuntu uses GNOME, and they differ in many ways).

---

### Post by Sef on 2006-11-10
> (Kubuntu uses KDE for the desktop, Ubuntu uses GNOME, and they differ in many ways).

The backends are the same; only the desktops are different.  Although there are differences between them, once you learn one then you can learn the other one if you so desire.

---

### Post by bodhi.zazen on 2006-11-10
> **iteyoidar said:**
> Like if I try to install Ubuntu 6.10(or whatever the newest one is) from the CD, what do I do to make sure it doesn't try to reformat my hard drive or install over my Windows partition?  Thanks.

To answer this question; Just install 6.10. You should have no problems.

[Install guide](http://www.psychocats.net/ubuntu/installing)

With that said, backup is prudent.

---

