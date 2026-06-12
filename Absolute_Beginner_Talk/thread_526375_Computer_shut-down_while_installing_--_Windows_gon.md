---
title: "Computer shut-down while installing -- Windows gone"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-08-15
I messed-up while installing Edgy to my laptop.  I was relying on my battery
and left while Edgy was being installed.  Now, of course, I can't boot
into Windows 2000 that was installed and if I try to install Edgy now, I
only have two options, format the whole disk or manual partition.

Can I resurrect the Windows that was installed or is it gone?

Thanks,
Michl

---

### Post by Steve1961 on 2007-08-15
Boot from a live CD and issue the command:

sudo fdisk -l

This should tell you if your windows partition is still on the disk.

---

### Post by Michl on 2007-08-15
Looks like the Windows partition is still on the disk:

> Device Boot    Blocks              Id      System
 /dev/hda1      20948728          c      W95  FAT32 (LBA)


So what can I do now?

Thanks for the help!!
Michael

---

### Post by Steve1961 on 2007-08-15
I'm not that familiar with windows 2000, but if it works like xp you need to boot from the installation disk and enter the recovery console.  Once done issue the following commands:

fixmbr
fixboot

and possibly:

chkdsk /r

then type exit and reboot.

---

### Post by Michl on 2007-08-15
> **Steve1961 said:**
> I'm not that familiar with windows 2000, but if it works like xp you need to boot from the installation disk and enter the recovery console.  Once done issue the following commands:

fixmbr
fixboot

and possibly:

chkdsk /r

then type exit and reboot.

I did all three, exited, rebooted and still can;t boot into windows off the
hard drive.  I will run it again without doing chkdsk.

By the way, I have a choice betwee recovery console and
emergency repair.  Maybe I should do emergency repair?

Michael

---

### Post by Steve1961 on 2007-08-15
> **Michl said:**
> I did all three, exited, rebooted and still can;t boot into windows off the
hard drive.  I will run it again without doing chkdsk.

By the way, I have a choice betwee recovery console and
emergency repair.  Maybe I should do emergency repair?

Michael

If memory serves you will need an ERD for that option.  Did you create one before the problem?

---

### Post by Michl on 2007-08-15
Nope, but there is an option for missing ERDs.  But that
did not help.

So I guess I am stuck with setting-up Windows again.
Fortunately, nothing was on it that isn't elsewhere.
Still would be nice to do it by recovering the old
installation.

---

### Post by Steve1961 on 2007-08-15
Unfortunately win 2000 doesn't have a straightforward repair install option like XP so I'm sorry to say that I think you're going to have to start from scratch.

---

