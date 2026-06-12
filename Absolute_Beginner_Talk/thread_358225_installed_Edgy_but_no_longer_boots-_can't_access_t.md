---
title: "installed Edgy but no longer boots- can't access tty"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Pollywoggy on 2007-02-10
I have installed Edgy twice, I used a Dapper CD to install the bare system, then I did a dist-upgrade to Edgy, but something that got installed later, after a couple of reboots, messed things up.

This is what happens when I boot.  The machine will stop booting and it leaves me at a (initramfs) prompt, with this error:

/bin/sh: can't access tty; job control turned off

I have Googled for a fix and I see that lots of people have this problem but I can't find a fix.  I could install the system again but since I don't know the cause, I don't know how to prevent a recurrence.

I don't want to have to install Debian Etch again, so please, someone tell me what is going on here.

It appears as though the problem might be caused by VMware overwriting the initrd.  Is that possible?  Both times this happened, I had just installed VMware Workstation.  If that is the cause of this, I will have to either reinstall kubuntu and leave out VMware (I need it) or else install something like Freespire.  I was using Debian Etch and I did not have this problem, but installing Debian is very tedious and I don't want to do that.

thanks

---

### Post by Pollywoggy on 2007-02-10
Is there a way to use a rescue disk to rebuild the initrd without having to reinstall ?

---

### Post by Pollywoggy on 2007-02-11
I think this problem was caused by something going wrong with the dist-upgrade to Edgy from Dapper.

I downloaded an Edgy iso after a few minutes of searching for one.  This meant not having to upgrade and I have a working system even after installing VMware.  I read somewhere that VMware can cause similar problems but in those cases, people were using RAID and I am not using RAID.

It's a good thing I did not have to abandon Ubuntu on this machine and install a different Linux.
I had been running Debian Etch.

---

