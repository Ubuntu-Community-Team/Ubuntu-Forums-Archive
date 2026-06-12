---
title: "I think I just hosed the kernel."
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by tjvanwyk on 2007-04-05
Just did a full format and fresh install of Kubuntu Feisty.

I was in the process of doing the normal post-install stuff - removing some packages, adding others, updating, and starting to pull some files over from my backup to the laptop.

And my computer overheated and shut down midway through the Adept update process.  Now when I try to boot, it goes through the BIOS and GRUB fine, but the Kernel panics:

> 
[6.759173] Kernel panic - not syncing: VPS: Unable to mount root fs on unknown-block(0,0)
[6.759220]


Then... silence.  It just chills indefinitely.  I went into GRUB, and the recovery mode kernel panics too, but flushes more output first.

So, I'm guessing the overheat occured halfway through the kernel update. Is there any way to salvage the kernel and the install, or will I have to start fresh?

---

### Post by cantormath on 2007-04-05
> **tjvanwyk said:**
> Just did a full format and fresh install of Kubuntu Feisty.

I was in the process of doing the normal post-install stuff - removing some packages, adding others, updating, and starting to pull some files over from my backup to the laptop.

And my computer overheated and shut down midway through the Adept update process.  Now when I try to boot, it goes through the BIOS and GRUB fine, but the Kernel panics:



Then... silence.  It just chills indefinitely.  I went into GRUB, and the recovery mode kernel panics too, but flushes more output first.

So, I'm guessing the overheat occured halfway through the kernel update. Is there any way to salvage the kernel and the install, or will I have to start fresh?

regarding the overheating issue, I put my laptop on a fan when i am doing the intial installation.  Its an acpi problem.
I would probably just reinstall and keep it cool.

---

### Post by cloneofme on 2007-05-13
> **tjvanwyk said:**
> Just did a full format and fresh install of Kubuntu Feisty.

I was in the process of doing the normal post-install stuff - removing some packages, adding others, updating, and starting to pull some files over from my backup to the laptop.

And my computer overheated and shut down midway through the Adept update process.  Now when I try to boot, it goes through the BIOS and GRUB fine, but the Kernel panics:



Then... silence.  It just chills indefinitely.  I went into GRUB, and the recovery mode kernel panics too, but flushes more output first.

So, I'm guessing the overheat occured halfway through the kernel update. Is there any way to salvage the kernel and the install, or will I have to start fresh?

That happened to me too, all i did was a clean wipe with gparted and installed again.

---

