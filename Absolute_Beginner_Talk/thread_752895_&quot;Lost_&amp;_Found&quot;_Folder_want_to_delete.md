---
title: "&quot;Lost &amp; Found&quot; Folder: want to delete"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by peterkeyani on 2008-04-12
Hi

I have a old NEC Pentium 4 1.5G with 630 MB of RAM and 2x20GB hard drives.

I have ubuntu 7.10 gutsy on one drive and the other is empty apart from a folder called "Lost & Found" with about 0.5GB which cannot be opened or deleted.

How can I get rid of it please?

Thanks for your help!

Pete

---

### Post by brian_p on 2008-04-12
> **peterkeyani said:**
> Hi

I have a old NEC Pentium 4 1.5G with 630 MB of RAM and 2x20GB hard drives.

I have ubuntu 7.10 gutsy on one drive and the other is empty apart from a folder called "Lost & Found" with about 0.5GB which cannot be opened or deleted.

How can I get rid of it please?

Thanks for your help!

Pete

Partition the drive with cfdisk or fdisk. Remove the file with rm -r. Sudo required with the commands.

---

### Post by ibutho on 2008-04-12
You can delete most files and directories as the admin user, with "sudo rm -rf". Use this command carefully because if you make any error, you can cause irreversible data loss or hose your system.

---

### Post by peterkeyani on 2008-04-12
> **brian_p said:**
> Partition the drive with cfdisk or fdisk. Remove the file with rm -r. Sudo required with the commands.

Thanks but Im new and therefore stupid!

What do I need to enter and where?

pete:confused:

ps i used to have ubuntu 7.10 on the second hard drive as well as the first but i removed it using gparted leaving the "lost and found" folder

---

### Post by ibutho on 2008-04-12
You can use gparted again if you wish. I believe its installed by default in Ubuntu (if not you can just install it yourself). I personally would boot from the live cd and then use gparted from there.

---

### Post by louieb on 2008-04-12
> **peterkeyani said:**
> ..."Lost & Found"...How can I get rid of it...

Good question. You can delete it. but its a ext3/2 file system folder.  I've never been able to permanently get rid of it. Linux will create one the  next time it rus fsck.

> /lost+found/ ... This is where files recovered during a file system check (fsck) are placed. I like to think of it as similar in its temporary nature to the Windows RECYCLER folder, but it isn't really the same purpose. (Windows places deliberately deleted files in RECYCLER until you empty the Recycle Bin.) In reality, the Windows chkdsk utility saves recovered fragments directly in the root.

from: [http://opencomputing.blogspot.com/2006/12/welcome-to-your-linux-filesystem.html](http://opencomputing.blogspot.com/2006/12/welcome-to-your-linux-filesystem.html)

---

### Post by forestpixie on 2008-04-12
As louieb says it get's created again - but if there is stuff in there you can get to it through nautilus if you open it as root easily enough and delete the contents once you know what they are. I'd be more interested in what was in there myself.

```
gksudo naultilus
```

---

