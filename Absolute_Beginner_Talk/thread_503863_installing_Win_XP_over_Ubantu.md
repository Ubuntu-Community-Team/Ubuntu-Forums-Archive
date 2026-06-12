---
title: "installing Win XP over Ubantu"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-07-18
want to install XP on my PC which already has Ubantu. I want to use the available free space on the HDD for installing XP.

Any guidance. ?????

Also want to know hou will i re-install the GRUB

pkj

---

### Post by Hobo Joe on 2007-07-18
Make some empty space on the drive with GParted, then put in the windows disk and install on the unpartitioned part of the drive.

You'll have to repair grub afterwards.

---

### Post by pkj on 2007-07-18
Thanks

Few mundane questions

How to get Gparted and how to use it..

How to repair the Grub at the end

pkj

---

### Post by Hobo Joe on 2007-07-18
Boot up the liveCD, then go to System>Applications/Administration(not sure which one)>GParted.

Then select a partition that has some free space, preferably at the END of the partition table, and resize until there is the desired amount of free space at the the end. Save the changes and boot into the Windows CD.

When asked which partition, select 'unallocated space', and format it to NTFS.

As for fixing GRUB, I'll post back in a minute, I need to do some hunting to find a good link.

---

### Post by pkj on 2007-07-18
OK I have downloaded Gparted Live CD (iso image) but am unable to figure out as to how to use it

pkj

---

### Post by pkj on 2007-07-18
I have copied the iso image on the CD and will be booting from it.

Thanks for all the help

waiting for the Grub re-installation details

pkj

---

### Post by Hobo Joe on 2007-07-18
Burn it as an .iso file. I would use Gnomebaker.

```

sudo aptitude install gnomebaker

```

Then go to tools>burn CD image, and select the file, then you'll have a bootable disk.

---

### Post by Hobo Joe on 2007-07-18
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

This will have the info you need. Including how to partition at the start.

---

### Post by pkj on 2007-07-18
Thanks once again

pkj

---

### Post by Hobo Joe on 2007-07-18
No problem, post back if you have anymore issues! :)

---

### Post by Gone fishing on 2007-07-18
You could just use the Gparted on the live ubuntu cd system>administration>gparted or install it using Synaptic. You will then need to fix grub have a look at

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Hobo Joe on 2007-07-18
> **Gone fishing said:**
> You could just use the Gparted on the live ubuntu cd system>administration>gparted or install it using Synaptic. You will then need to fix grub have a look at

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

That's what I told him to do. :)

Although I did use a different link, but same idea.

---

