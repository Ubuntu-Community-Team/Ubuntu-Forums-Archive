---
title: "xp os on memory stick.....(brainstorming)"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by determinedblkman1 on 2007-12-05
just an idea,  who thinks it's possible to format a (lets say a 4gb) memory stick (w/ ntfs)  using linux w/ the grub boot loader but windows OS 

now possible roadblocks--  since the usb is a scsi device the bios (for some comps this might not be possible)  would have to be set. however, it would be ideal to be able to emulate a boot (i've seen this done w/ the linux "crossover" program) this would make it possible to plug it in & initialize.

this is just an idea, if anyone has a way to make this a reality, or point out anymore possible obstacles i ask that you point them out to me. 

   appreciate your help

---

### Post by ItsMitsHere on 2007-12-05
> **determinedblkman1 said:**
> just an idea,  who thinks it's possible to format a (lets say a 4gb) memory stick (w/ ntfs)  using linux w/ the grub boot loader but windows OS 

now possible roadblocks--  since the usb is a scsi device the bios (for some comps this might not be possible)  would have to be set. however, it would be ideal to be able to emulate a boot (i've seen this done w/ the linux "crossover" program) this would make it possible to plug it in & initialize.

this is just an idea, if anyone has a way to make this a reality, or point out anymore possible obstacles i ask that you point them out to me. 

   appreciate your help

I think you can do it simply by booting from xp install cd and installing the os on a memory stick. If xp install disk does not recognize usb disk, you can copy an image of XP installation on usb disk via so many alternatives. I think booting from xp is possible 'coz sometimes i restart my comp with usb stick connected, It tries to boot from it and fails ;).

Another alternative is install any linux on usb stick (easy :)) and then make dual-boot linux-xp and then delete linux (but not grub). Yet another option may be rEFIt.

Let me know what do you think?

---

### Post by irish_flu on 2007-12-05
Not exactly the method you were looking for, but you *do* end up with Windows on a stick, check out "Bart PE":
[http://www.nu2.nu/pebuilder/]("http://www.nu2.nu/pebuilder/")

---

