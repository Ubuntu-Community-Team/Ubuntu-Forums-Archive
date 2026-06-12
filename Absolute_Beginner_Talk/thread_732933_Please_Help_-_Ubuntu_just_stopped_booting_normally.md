---
title: "Please Help - Ubuntu just stopped booting normally this morning"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Cold-Gin on 2008-03-23
Hi. My machine has been booting fine until just this morning. Normally, it takes a long time for the login screen to come up, so from the boot loader menu I usually do:

e to edit
---> highlight kernel line, then press e
--------> Remove quiet and splash directives
--------------> Press enter then b to boot

I have not applied any new updates, and have booted fine multiple times since the last update. Now, the login screen does not come up whether I follow the steps above, or if I let the machine come up on it's own. After fifteen minutes, I just have a blank screen.

What can I do to be able to bring up the login screen? I'm not really linux savvy, so could you please describe the exact steps to debug and/or bring up the login screen?

Thanks so much.

---

### Post by Dr Small on 2008-03-23
So it is just a blank screen you say?
Have you tried changing to Virtual Terminal 1 or 7 to see if the system is really booted?

---

### Post by spiderbatdad on 2008-03-23
Please tell us what version you are running, and what kernel.```
uname -r
```

---

### Post by Cold-Gin on 2008-03-23
Thank you for responding.

```


Have you tried changing to Virtual Terminal 1 or 7 to see if the system is really booted?


```

No. I'm sorry, but I am new to Ubuntu and Linux. Can you explain?

Version and system information:

Ubuntu 7.10
Kernel: 2.6.22-14 generic

System:

Gateway 300X
Celeron 1.8GHz processor
768MB ram

Thanks so much again for any light that you can shed.

---

### Post by Dr Small on 2008-03-23
You would press CTRL + ALT + F1 to change to Virtual Terminal 1, and CTRL + ALT + F7 to change to Virtual Terminal 7.

Also, another question, have you tried booting into recovery mode to see if it will completely boot?

Dr Small

---

### Post by Cold-Gin on 2008-03-23
When I get the blank screen, I tried to do <CTRL> + <ALT> + <F1>, but it does not respond. I also tried choosing the recovery kernel mode option, but again, the blank screen just stays frozen.

Is there anthing that I could do from the GRUB menu that might help, even for diagnostics?

Thanks again.

---

### Post by bhold on 2008-03-23
Might be time to download super grub disk. Great tool, I have used it several times to recover messed up grub environments.  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

You can also re-install grub from Ubuntu live cd - I haven't done that yet myself, others can provide you with more detail. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Cold-Gin on 2008-03-23
Thank you. I just burned the super grub CD... Any suggestions on what to do first? Will anything I do with super grub wipe out what's on the drive?

Thanks again.

---

### Post by Cold-Gin on 2008-03-23
Just tried the super grub CD. I was able to walk through the menus, but the OS still hangs on a blank screen after the boot is attempted (after it gets passed the GRUB menu).

Now, I also have another version of the kernel available to me in the GRUB menu, and that is  2.6.20.
I selected that version, and I got the Ubuntu status bar splash screen. After a while, I got a black diagnostic screen that had a lot of verbage, and at the end said:

"An automatic file system check (fsck) of root file system failed. A manual fsck must be performed and then the system restarted. Press CONTROL-D..." When I pressed CONTROL-D, it put me back to the GRUB menu.

Question: Can this previous version of the kernel help me repair the problem (can I boot into this version to do fsck somehow, and then go back to the later version of the kernel afterwards)? If so, when I get back to the GRUB menu after the fsck message, what should I do? Use the repair version of the previous kernel?

Thanks for any advice that you may have. If you can be as detailed as possible, I would be very appreciative.

---

### Post by Cold-Gin on 2008-03-23
Could running fsck help me? I do not know how to run it safely. If this would be an option, can someone tell me exactly how to run fsck safely?

Thanks!

---

### Post by Dr Small on 2008-03-23
Well, you can not run fsck without access to a terminal, so...
Although it probably can be done from a livecd, but I have never tried so that is not conclusive proof that you can.

---

### Post by Cold-Gin on 2008-03-23
I can get access to a terminal if I boot into the earlier version of the kernel (2.6.20). Would this be OK? If so, could you give me the commands for running fsck safely?

I read that you need to unmount the drive first. Could I do the following without damaging anything?

sudo umount /dev/sdb1
sudo fsck

I'm sorry to keep bugging you, but I am in bad shape without being able to access my Linux drive right now.

Thanks so much.

---

### Post by bhold on 2008-03-23
If it was my system I would proceed as follows at this point:

1. I would go ahead and run the fsck. If you are worried about it, you can run it in "safe" mode with the -N option to show what operations will be done, but without actually doing anything. This might give you a better idea of what file system problems, if any, you are up against.

2. If you do not have a current backup, try to get your personal data backed up. Might be able to do this by booting off the live cd, mount your hard drive, and copy the required files to dvd or cd, or another hd, depending on what hardware you have available.

3. Next I would look at the /boot/grub/menu.lst file on your hd using the editor of your choice to see if anything looks obviously messed up. Maybe the super grub disk lets you do this? Been a while since I have used it and don't remember.

4. Have you re-installed grub? If not, do so. This will make sure the mbr points at the correct grub files, in case the mbr has somehow been corrupted. Again I think this can be done using super grub.

5. If all else fails, and assuming you have all of your necessary personal data backed up - might be time to try re-installing Ubuntu.

And if this turns out to be a hardware problem, none of the above is likely to do much good - other than to point out that you might have a hardware problem.

But most of all, try to get your personal files backed up. Everything else - hardware and software - can be repaired.  Good luck.

---

### Post by Cold-Gin on 2008-03-23
I fixed it.

First, let me thank all who replied, and tried to help. Also, let me thank those who posted 
information in other posts about fsk, and being sure to umount the drive first. Next, here is exactly how I fixed it:

1.) Tried to boot via a previous kernel version that was available through my GRUB menu
     (2.6.20)
2.) Got an error page as expected, but at the end of the error page, a message read:

"UNEXPECTED inconsistency: Run fsck manually (ie without -a or -p options)
fsk died with exit status 4"

3.) At the end of error page, it allows you to login as root from a command line
4.) Ran umount /dev/sdb1
5.) Ran fsck -y /dev/sdb1
6.) Rebooted, and at the GRUB menu, chose the latest version of the kernel (2.6.22)
7.) Now, I got the blank page again, BUT, I pressed <CTRL> + <ALT> + <F1>,
     got a blank screen with a single cursor in the corner, waited about a minute,
     and the login window, and then desktop finally came up.

The file system looks fine from what I can see. Everything is in tact.

Thanks again.

---

### Post by Cold-Gin on 2008-03-23
PS - After running fsck -y /dev/sdb1, there were also messages listed on the screen that stated that a node had been fixed.

---

### Post by Dr Small on 2008-03-23
Awesome! Glad you got it fixed :)

---

