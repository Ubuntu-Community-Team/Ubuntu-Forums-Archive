---
title: "HP L2000 Install Runs Forever at Partition"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by ubu40 on 2007-02-21
Have an HP L2000 laptop with Turion64 WinXP home edition, version 2002 service pack 2, mobile technology. Bought Ubuntu Unleashed with 6.06 LTS disk included. When using this disk to attempt a dual boot, install runs forever at partition section (it ran four hours with no results. Had to turn off system to stop and eject disk). Downloaded the 6.06 LTS for AMD 64 and got same results. Also, of appx. 100GB, 76.6 available, Ubuntu says disk full when trying to partition 50/50 (not sure if this is related to the first problem).

Question1: How long should the partition device take?
Question2: What is the fix for this situation?

Additional information can be provided and any help is greatly appreciated.

Thank you in advance and free coffee (or whatever beverage you prefer) on the house!

- ubu40

---

### Post by tgalati4 on 2007-02-22
Here's a reach--go into the HP BIOS and turn off disk drive LBA translation.  Sometimes the bios treats large drives differently and causes the Live disk to misread the partition table.  The live disk shouldn't take more than 5 minutes to come up.  Anything longer than that is a hangup.

Let us know what you think of the book.  With so many web resources available, does the book help you?

---

### Post by ubu40 on 2007-02-22
OK, I tried to adjust the LBA setting in the BIOS setup, but there is no switch to set. Apparently, HP/Compaq places this setting in the software. So, I upgraded my BIOS from F.08 to F.27 (I guess the HP software update does not pick up the BIOS). Anyway, I tried the install again and it ran for 30 minutes before I cancelled it.

My next step is to use a third party partition device and then install Ubuntu directly to the new partition. I have never done this before. I have dual boot installed Caldera 2.3 on a Compaq laptop with their partition utility and have partitioned a second hard drive on a desktop using Red Hat 6.2. I'll let you know how it turns out.

Lastly, I will let you know about the book. I blew through the first 60 or so pages because I was already familiar with the material. I was hoping for some insight into these newer Linux distributions, but I suspect that I will not find it in the book.

Thank you in advance for any additional replies!

---

### Post by tgalati4 on 2007-02-22
Well, it's good to run with the latest BIOS.  You will find that there is a lot of sharing between Linux distributions--combining of DNA if you will.  I started with Red Hat 6.0 myself.  I still have the 8" thick book.  I use it to prop up a dual -screen display.  Ubuntu is based on Debian.  The Debian website has decent documentation and there are several resources on the web that show how all of these distros compare.

Did you perform a check of the CD.  There is a menu pick to inspect the checksum of the disk.  Perhaps you got a badly-pressed CD.  It happens.

There could be a problem with the Windows hibernation file.  This is usually created with an HP utility and resides on designated tracks on the drive.  It could be that the partitioner is taking a dump because of this file.

You could turn off hibernation in Windows and turn it off in the BIOS and just not use hiberation in Windows.  This is a pain, because most folks want to hibernate windows go into Linux and then go back to windows.  Hibernation is quicker than booting windows from scratch.  Because the BIOS controls the location and writing of this hibernation file, it may be tripping up the partitioner.

---

### Post by ubu40 on 2007-02-23
You must have super BIOS. Mine looks like the BIOS on an old AT machine...a few screens with one or two options.

Like the LBA, there was no switch in the BIOS for hibernation. So, I went to power management and unchecked the hibernation. The install ran for about an hour, at the partition section, before I cancelled the action and rebooted.

Maybe when I have more time, I will partition the hard drive first and then try to do the install.

Again, thank you for the advice.

---

### Post by tgalati4 on 2007-02-23
You could have a defective drive.  It's possible that there is a bad spot on the drive that the partitioner gets hung up on.

When you partition the drive outside of the installer, you should be able to format each partition and see if the drive is writeable on each partition.

Of course if parted or cfdisk have problems partitioning outside of the installer then there is a deeper problem.

Did you perform the CD selfcheck?  You want to make sure that disk is OK.

The BIOS hints were based on Dell machines who have switches to change power management in the BIOS.

Keep the faith.  We want you to join the revolution.  Here's your beret and bandolier.  Watch your head on the way out.

---

### Post by ubu40 on 2007-02-23
Yes, I did check the distribution and download disks and it had no errors. However, my BIOS did have a Disk Check function. It said it was estimated to run 86 minutes. It ran for over two hours!

Therefore, I now suspect that my hard disk is corrupt. I'm going to try some third party software to see if I can repair or uncover the problem. It could also be a software issue. I'm running a bunch of Norton junk and other software.

I'll keep this issue open until I run some checks on my hard disk.

---

### Post by ubu40 on 2007-02-23
Problem solved!

I had to reach far back into the old DOS days to find the solution. Apparently, my hard disk was corrupt. I ran chkdsk c: /f /r. I now have a dual book HP L2000 split 50/50. So, to summarize:

1) Update your BIOS (not the problem, but a good idea).
2) run chkdsk c: /f/r (or whatever chkdsk you prefer).
3) Consider deleting Windows permanently.

Anyway, thank you for the assistance and thanks for the beret and bandolier.

Barista! Coffee all around (or whichever beverage you prefer)!

---

### Post by tgalati4 on 2007-02-23
Great news.  We must continue the resistance.  Viva La 'Buntu!  Barista! Cerveza pronto pronto.

---

### Post by ubu40 on 2007-02-24
One last note to add to the success story. This message is being posted using Ubuntu, FireFox and a wireless connection! I was able to configure the wireless connection using the advice found in the following link:

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom).

Thank you.

---

### Post by tgalati4 on 2007-02-24
That's great news.  Now share your disks and knowledge with others.

---

