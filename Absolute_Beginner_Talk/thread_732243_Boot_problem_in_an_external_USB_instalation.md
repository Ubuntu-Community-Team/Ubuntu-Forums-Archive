---
title: "Boot problem in an external USB instalation"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by aduplat on 2008-03-22
Hi:

I already made a mistake. I installed Ubuntu 7.10 in an external USB HD and I omitted to disconnect my master HD. For this reason... right now I have to keep connected the USB HD in order to access to windows.

What can I do to resolve this problem?

The other dilemma is that I need to recover the old windows MRB and I dont know how to do this.

I appreciate all your help.

---

### Post by slackmaster on 2008-03-22
aduplat,

So Ubuntu will run on any compatible computer from the external HD, but windows will not boot unless the external HD is connected?  


I'd use Ultimate Boot Disc for Windows to access your windows installation.  It is a live windows CD chock full of more utilities than you will ever need.  It takes a little while to create the disc, but once you do, it is a very useful tool for any future windows issues.  

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)


But for your situation, it can get your windows installation working again;  it can recover the MBR.
Before you make any changes to your windows installation, I'd recommend backing up all your valuable files with the boot disc.

Once you get windows working again, then try your Ubuntu OS.   Hopefully you will be able to run windows without the external HD.
Let me know how it turns out, and be sure to get a second opinion.  There might be a simpler solution.

Slack

---

### Post by dstew on 2008-03-22
What happened is that you installed grub to the MBR of the internal hard disk. This is the default option on the installer. Grub needs to get its stage2 file and menu from the external drive where Ubuntu is installed, so you cannot boot Windows from grub without the external drive being present.

I assume what you wanted was to be able to boot Ubuntu if the external drive was plugged in, but boot Windows if it was not plugged in. This depends on being able to boot the USB drive. Not all BIOSes can do that. Check to see if your computer's BIOS can boot the external drive. If so, you can re-install grub to the MBR of the external drive, and then configure your BIOS to boot it. If your BIOS cannot boot the USB drive, you will need a boot floppy or other trick to boot the Ubuntu system.

It is easy to recover your WIndows boot. Use the Recovery Console on your Windows CD. The command is **fixmbr**. If you don't have a Windows CD, you can also run fdisk /fixmbr from a Windows 98 rescue floppy. I think the [supergrub disk]("http://supergrub.forjamari.linex.org/") can fix a Window MBR also.

---

