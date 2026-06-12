---
title: "Critical Problem! Please Help!!"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by McMagic on 2008-04-07
My computer has been running ubuntu more reliably then vista for quite some time, and just recently i was downloading an album torrent file with deluge, and i got an error message saying that my disk drive had been changed to a read only state. the computer then proceded to freeze, and upon reboot, suspends in a black screen with blinking cursor. When i attempt to boot in recovery mode, it says that my partion is in read-only state and leaves me with a command prompt. Here is my question:

WHAT IS THE CODE TO CHANGE MY PARTION OUT OF READ-ONLY STATUS?

this is pretty urgent as i have some homework files on there that need to be done by tomorrow. Thank you so much for anyone who relies to this!

---

### Post by tamoneya on 2008-04-07
have you been playing with fstab.  Please post /etc/fstab and we should be able to fix it.

---

### Post by InfinityCircuit on 2008-04-07
Boot into single-user mode (you should be able to do this from the grub menu).

Run:

```
mount -a -o remount,rw
```

That will temporarily fix the problem.  Then post your /etc/fstab.

---

### Post by McMagic on 2008-04-07
i really havent been touching any settings, and cant understand why it did this. after i type in the mount command, what do i do?

---

### Post by tamoneya on 2008-04-07
post the contents of
```
sudo nano /etc/fstab
```

---

### Post by McMagic on 2008-04-07
> **InfinityCircuit said:**
> Boot into single-user mode (you should be able to do this from the grub menu).

Run:

```
mount -a -o remount,rw
```

That will temporarily fix the problem.  Then post your /etc/fstab.

"remounting is not supported at present. you have to unmount and then mount it once again."

kind of a mean error message.

---

### Post by igknighted on 2008-04-07
Try booting the liveCD and mounting your disks to check and see if everything is still there.  Sounds like a hardware failure to me TBH.

---

### Post by McMagic on 2008-04-08
Wow, Im so disappointed. Its HDD failure to be sure, i can hear the platters clicking now. I almost wish my primary drive with Vista had been the one to go... oh well i guess i buy a bigger, faster drive to run ubuntu on!

sucks *** that i lost all of those settings....
is there any way i might be able to recover this?

---

### Post by igknighted on 2008-04-08
> **McMagic said:**
> Wow, Im so disappointed. Its HDD failure to be sure, i can hear the platters clicking now. I almost wish my primary drive with Vista had been the one to go... oh well i guess i buy a bigger, faster drive to run ubuntu on!

sucks *** that i lost all of those settings....
is there any way i might be able to recover this?

You *should* always back everything up, as hard drives are really fickle things that do die randomly.  If you have a backup, you can copy the config files to the new install (esp your /home).  I think if you boot the liveCD you could try to save your /home to the other disk.  It's possible that that portion of the disk is still readable.

Lesson: Any data on a hard drive is at risk.  Always back up.  Hard drives are NOT safe, permanent storage.

---

### Post by McMagic on 2008-04-08
Duly noted. I actually have a 500 gig external on which i keep regual backups of media and stuff. but school work i didnt really think about i guess.. i only lost like 2 assignments though, so whatever.

Ok, so i have removed the faulty drive and left in my primary with Vista on it. I am typing this from livecd, however, because if i try to boot from the primary HD the grub menu still tries to load, and then halts with Error 21.

how do i take off the grub menu until i get a new drive to put ubuntu on?

---

### Post by riven0 on 2008-04-08
You'll have to restore Windows MBR. You can either do this through your Windows CD. Or, if you don't have it, burn the Super Grub Disk and follow instructions from there. 
[URL="http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"]

Super Grub Disk[/URL]

---

