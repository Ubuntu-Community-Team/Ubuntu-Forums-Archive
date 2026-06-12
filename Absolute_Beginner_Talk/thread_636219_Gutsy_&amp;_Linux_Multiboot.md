---
title: "Gutsy &amp; Linux Multiboot"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Jerry N on 2007-12-09
Twice when I have installed Gutsy on a drive already containing a Linux distribution (LinuxMint 4 in this case) on another partition, the Linux installed first will no longer boot, giving a "File System Check Failed" message.  The use of "CTRL-D" will allow LinuxMint to start but the problem repeats itself on a reboot.  I don't think this ever happened to me when I installed Feisty on a drive already containing other versions of Linux.  Is this a bug in Feisty?

Second question:  Is it a good idea to allow two Linux distributions to share a "/home" partition.  It appears that the two distributions interfere with each other.

Jerry

---

### Post by jken146 on 2007-12-09
I'm not sure I can help you with your first question, but for the 2nd, yes, multiple linux distros can interfere with each other if you have a shared /home partition.  This is because of all the hidden files that each one puts in /home/<username>.  Press Ctrl+H in Nautilus to see them.

One solution is to have a seperate /home for each distro and store your personal files somewhere else (or in one of the /home's), keeping the same username in each installation.

---

### Post by rsambuca on 2007-12-09
The first issue is because your UUID numbers for the partition has changed when you installed the second OS.  Just edit your fstab and you will fix it permanently.

As for shared /home, yes you can, but make sure you use different usernames so things don't get to messed up.  Like the previous poster, I prefer to have a shared /media partition instead.

---

### Post by uidb4056 on 2007-12-09
The second question:
I wouldn't recommend this unless you will have different users in each Linux in order to preserve specific data of each Linux.

---

### Post by rsambuca on 2007-12-09
> **uidb4056 said:**
> The first question;

When you install a Linux distro and you let that install the GRUB botloader then the MBR is overwritten  and you will lost your previous settings. Ubuntu installs is able (like some others) to detect the existence of other OS in the disk partions like windows or other Ubuntu releases and adds them automatically to your boot menu.

I hope that in this case Ubuntu has not recognized your LinuxMint and that is the reason in this case you can boot from it.

I hope this can be patched in order you can boot from both Linux, if you can mount the partition where you have LinuxMint then please post the file /boot/grub/menu.lst to give you suggestions how to do it.


This is incorrect.  The OP's problems are due to UUID mismatches, not grub errors.  In any event, an easy fix.

---

### Post by Jerry N on 2007-12-09
rsambuca wrote:  > **rsambuca said:**
>  The first issue is because your UUID numbers for the partition has changed when you installed the second OS.  

I assume that I am to edit the fstab in the partition that failed to boot properly but exactly what should I be editing?  I tried changing the UUID in fstab for the partition in question to the value that was referenced in the boot error message but that did not fix the problem.  

Jerry

---

### Post by rsambuca on 2007-12-09
Yes, you want to edit the fstab file on the mint partition.  You can use the command 'blkid' to get the correct UUID number, then edit the /etc/fstab to match.  As an alternative, you can just remove the UUID number entirely and use the /dev/hda type designation.  Both work.

If you think you may be distro hopping for a bit, you might want to use the /dev/... designation since the UUID will change everytime you format and install a new distro.

---

### Post by Jerry N on 2007-12-09
I am playing with a number of different distros (mint, freespire, linspire etc) but I don't see that any of them have an advantage over UBUNTU.  But I am a tinkerer so will probably continue playing.

Thanks for the info and I will yell again if I am still in trouble!

Jerry

---

