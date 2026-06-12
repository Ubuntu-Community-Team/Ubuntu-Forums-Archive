---
title: "[SOLVED] Grub Problems and Issues"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-08
Ok. I have 2 hard drives installed on this machine.

Hard drive 1 (master) has Ubuntu 7.10 installed on it.
Hard drive 2 (slave) has Ubuntu 7.04 (CLI) installed on it.

So, hard drive 1 is my desktop and hard drive 2 is my server.

I have looked in gparted, and it identfies them as the following:
Hard drive 1 (Desktop) /dev/hdc
Hard drive 2 (Server) /dev/hdd

Right now, I have set the boot order up in my BIOS to boot the slave (hard drive 2, server) first, but even if I do try to boot the master (hard drive 1, desktop), GRUB spits out an error at me.

For the record, Ubuntu 7.10 was installed on the hard drive first, and I never unplugged either drive (which was probably a big mistake on my end). Both are brand spankin new installations, so if I ruin them, it's not problem to me.


So, here's what I want to do. I want to continue to boot Hard drive 2 (server) first, and at the GRUB menu, be able to choose to boot Hard drive 1 (desktop) from the menu, if this is possible, I have no idea about any of this, so any help would be appreciated!!!


I can only boot from Hard drive 2 (the server) right now, also.

Dr Small

---

### Post by durrell on 2008-01-08
All you need to do is make a new entry in the menu.lst of the GRUB installation that works. So it sounds like the server GRUB install works. Make a new entry in /boot/grub/menu.lst on the server partition that will add an entry for the master drive (desktop install).

---

### Post by Dr Small on 2008-01-08
Thanks for the advice, but how am I to know what entry to add to point to hard drive 1 (desktop) ?

Thanks again,
Dr Small

---

### Post by durrell on 2008-01-08
Well one way would be to mount the first drive and check what its GRUB entry is. I guess it would be "/dev/hdc" if that is how Gparted sees it. So mount whichever partition your GRUB install resides on (on the master drive) and see what the entry is.

Another option would be to reinstall GRUB on the MBR so that you can boot into the graphical desktop install. This would probably be easiest.

1. If an Ubuntu Live CD, type sudo grub, if a Rescue Disk, just type grub. This will enable a grub> prompt.

2. At the GRUB prompt, type find /boot/grub/stage1

3. This will return a (hd?,?) value (example: (hd0,2) (You will probably be looking for the one starting with (hd0 since your desktop install is on the master drive. It should return 2 values.

4. Now you have the location of your GRUB install. Next, you type root (hd?,?) where (hd?,?) is the value that you got from the find command earlier.

5. Once you've done that, type setup (hd?) PAY ATTENTION TO THIS STEP. It is not the partition (example: (hd0,2)), but rather the hard drive (example: (hd0).

6. After that, close everything and reboot..and you should get a GRUB screen.

Once this is done, assuming it goes to plan, you can mount your server disk, then copy and paste the GRUB entry to your menu.lst on the desktop disk. Then you should have access to both installs.

If there is an easier way, I don't know it.

---

### Post by Dr Small on 2008-01-09
Ok. Well now I have my problem solved, and got everything working the way I wanted it, so I'll try to explain what I did, since last night.

First, I erased both drives, completely. I intended to start over from scratch and get this right this time.

Second, I unplugged Hard drive 2, and installed Ubuntu 7.10 on Hard drive 1.
Third, I unplugged Hard drive 1, plugged in hard drive 2, and installed ubuntu cli on it.
Forth, I plugged hard drive 1 back in, and changed settings in the BIOS for boot order, and now both hard drives would boot from either OS.

Fifth, I booted up in Ubuntu 7.10 (off of Hard drive 1) and mounted hard drive 2. Went to /boot/grub/menu.lst and then brought the same up for Hard drive 1.
I copied the entry from Hard drive 1, and pasted it onto Hard drive 2's grub, and both were pointing to hd(0,0), so I thought that would be problems, and it was.

Saved it, rebooted, changed the BIOS to boot Hard drive 2, tried the GRUB menu, and GRUB couldn't find the file on hd(0,0) for the desktop (hard drive 1) OS.

So, I booted up in my server OS, edited grub from there, and changed it to, hd(1,0), saved, rebooted, and now it works :)

Now I can boot from either my server (on hard drive 2) or my desktop (on hard drive 1) right from the GRUB menu :D

Thanks for all the help!

Dr Small

---

### Post by durrell on 2008-01-09
So you likely could have done it without reinstalling, but as long as it worked that's all that matters. Glad you got it fixed.

---

### Post by Dr Small on 2008-01-09
Yeah, most likely, but I was so confused and all, so starting over from scratch and writing out the steps on paper really helped for doing it the second time :D

---

