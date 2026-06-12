---
title: "Laptop boots Ubuntu 7.04 CD, but won't install"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by JimR on 2007-04-26
I have a laptop (ASUS M3000N) which I was, and still am, able to successfully run and install Ubuntu 6.10 from the live CD.  As of right now the hard drive is wiped and I am trying to install Ubuntu 7.04 to it.  The 7.04 disk will boot, but when I select any of the install options it will go through the standard "Loading Linux Kernel" progress bar but then the computer will reboot.  This is not the case for the 6.10 disk, which will boot and install correctly.

Now I have tried the Ubuntu i386 Desktop cd, the Ubuntu i386 Alternate cd and even the Xubuntu i386 Desktop cd.  All were burned at 1x and the MD5 checksums were correct.  All of them did the same thing, they had the "loading linux kernel" progress bar then the computer rebooted back to the Ubuntu install screen.

I could not find anyone facing a similar situation in this forum, does anyone have any ideas?

Thanks.

---

### Post by supersonicdarky on 2007-04-26
perhaps you could install 6.10 and upgrade to 7.04?

if you dont find a better solution that is

---

### Post by JimR on 2007-04-26
> **supersonicdarky said:**
> perhaps you could install 6.10 and upgrade to 7.04?

if you dont find a better solution that is

Good call, the thought crossed my mind, but like you said I wanted to find a better solution and use that option as a last resort.

---

### Post by mac.ryan on 2007-04-26
> **JimR said:**
> does anyone have any ideas?

What I would try to do would be to change the boot params (I think is F6 from the initial menu of the liveCD). I would remove quite, splash (to see what's up) and eventually add noapic, irqpoll (to "simplify" the kernel launch and to bypass possible mistakes of the bios).

These are just ideas, though... if you boot the verbose way, it would be useful if you could report what are the "last words" of your computer before to reboot...

---

### Post by dislocated on 2007-04-27
I'm having a similar problem. Older Ubuntu's booted and installed fine, but now Feisty goes to a blank screen after the orange progress bar has bounced back and forth a while.

With quiet turned off, this is the last line of text:
[ 5.144000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher

Would love some help on this one.

---

### Post by bar10der on 2007-04-27
Sorry. misread your original question. I burnt my iso to fast and had the same problem but I see you burnt at 1X.

---

### Post by mac.ryan on 2007-04-27
> **dislocated said:**
> With quiet turned off, this is the last line of text:
[ 5.144000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher

Would love some help on this one.

The squashfs is a compressed read-only file system. I think it is used for the booting sequence only, for creating the ram disk the kernel uses before it is able to mount the real disks on your machine.

I don't know what specifically can be the cause of your problem, but I would check:
[LIST]
[*]the disk for errors (just in case the FS went corrupted)
[*]the RAM size (do you have enough for booting up?)
[*]the RAM health (RAM test from the ... it can take a while to run)[/LIST]I couldn't find any relevant bugs files in launchpad for this... :confused:

---

### Post by JimR on 2007-04-27
I removed 'quiet' and 'splash' from the boot parameters and text flashes very quickly over the screen right before it reboots, is there any way to slow down that information to make it readable? (The pause button doesn't work)

---

### Post by JimR on 2007-04-28
Well, with my handy digital SLR I was able to snap a picture of the last second of life Ubuntu 7.04 had before my computer restarted, here it is (with the leading numbers left out... are they important?):

```

[   ] Security Framework v1.0.0 initialized
[   ] SELinux: Disabled at boot.
[   ] Mount-cache hash table entries: 512
[   ] CPU: L1 I cache: 32K, L1 D cache: 32K
[   ] CPU: L2 cache: 2048K
[   ] Compat vDSO mapped to ffffe000.
[   ] Remapping vsyscall page to ffffe000
[   ] Checking 'hlt' instruction... OK.
[   ] SMP alternatives: switching to UP code
[   ] Freeing SMP alternatives: 11k freed
[   ] Early unpacking initramfs... done
[   ] ACPI: Core revision 20060707
[   ] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   ] ACPI: setting ELCR to 0200 (from 0830)
[   ] CPU0: Intel(R) Pentium(R) M processor 2.00GHx stepping 08
[   ] SMP motherboard not detected.
[   ] Brought up 1 CPUs

```

As far as I can tell that is the end of it before the computer restarts.

I added "noapic" and "irqpoll" to the boot options but the computer still restarts, I will try to see if the text displayed is any different than above.

---

### Post by mac.ryan on 2007-04-30
Difficult to say what it can be... if those are the very last lines (the timestamp really doesn't matter), i would investigate the way the kernel interacts with the bios, as there is no evident "culprit software" leaving a trace...

From the bios side: have you checked if there is any upgrade available with your bios? If there is a a "load safe settings" option in your bios, you might wish to try that.

From the kernel site: you could try to install Edgy (it has an older kernel). If it works, you could then try to do a dist-upgrade from Edgy (you can also run Edgy and insert the Feisty **alternate** CD into the bay: the option of upgrading should come up automatically and you won't have to download 400+ Mb of packages...

:confused:

PS: have you ran the RAM and disk tests?

---

### Post by CAsurfer on 2007-06-04
The problem is also documented in this forum: [http://ubuntuforums.org/showthread.php?p=2777288&posted=1#post2777288](http://ubuntuforums.org/showthread.php?p=2777288&posted=1#post2777288).

I have exactly the same problem.

I doubt it's a matter of data corruption, since I'm doing an install from the hard disk (plus the fact that other people are having the same problem).

I don't think it's a problem with my physical RAM memory, since the computer was working fine under another operating system.

The machine has 512MB of physical RAM memory.  I've tried playing around with the values I assign to ramdisk_size in the kernel line in grub, but to no avail.  Mac.ryan, is this what you meant by RAM size?

---

### Post by pappapump on 2007-06-04
I've seen this before and the solution that worked included reducing shared 
video ram to the lowest setting in bios.
The other problem involved a passworded hard drive, but that don't seem to be related to your problem.

---

### Post by CAsurfer on 2007-06-04
I looked at the bios settings, and I didn't see anything having to do with shared video RAM.

Any ideas where you saw this problem?

---

