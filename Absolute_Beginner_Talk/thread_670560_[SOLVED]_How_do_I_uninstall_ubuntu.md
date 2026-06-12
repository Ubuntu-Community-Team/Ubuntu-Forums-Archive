---
title: "[SOLVED] How do I uninstall ubuntu?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Mats_swe on 2008-01-17
Hi,

I want to uninstall Ubuntu 7.10 from my laptop with Windows Vista as well. Is there two things I need to do:

Start some Windows Bootloader instead. How do I do that?
Then just delete the partition with Ubuntu and the swap partition as well?

Is that correct?

---

### Post by kellemes on 2008-01-17
> **Mats_swe said:**
> Hi,

I want to uninstall Ubuntu 7.10 from my laptop with Windows Vista as well. Is there two things I need to do:

Start some Windows Bootloader instead. How do I do that?
Then just delete the partition with Ubuntu and the swap partition as well?

Is that correct?

You better "fix" your bootloader first by getting the Windows bootloader back. You can do this from the recovery-console of a Windows setup-disk, as far as I remember you have to enter "fixmbr" from the console, it will will reinstall the windows bootloader in the mbr.
You can also use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to reinstall the windows bootloader as far as I know.

After this you can safely delete or reorganize your partitions using whatever tool you want.

Edit: By the way.. always expect things to go wrong, eventhough most often it won't. ;-)

---

### Post by duruttye on 2008-01-17
Did you get a Windows repair dvd, or cd?

Because if you did, I think you can just delete the partitions or format them from vista, the when you reboot insert the repair cd, bott from it, and the cd repairs the MBR (master boot record) because thats what is rewritten when ubuntu is installed.

I hope that helps.

Why do you want to uninstall ubuntu?

---

### Post by Het Irv on 2008-01-17
Vista is supposed to have a partition manager but I cannot find it, but that is what you should use to uninstall Ubuntu.  Just out of curiosity why are you uninstalling Ubuntu?

---

### Post by Mats_swe on 2008-01-17
> **duruttye said:**
> Did you get a Windows repair dvd, or cd?

Because if you did, I think you can just delete the partitions or format them from vista, the when you reboot insert the repair cd, bott from it, and the cd repairs the MBR (master boot record) because thats what is rewritten when ubuntu is installed.

I hope that helps.

Why do you want to uninstall ubuntu?

I can't get ubuntu to work. It will not take my Video card, and it also stops when running local boot script.
I thought I should try Kubuntu or something else.

---

### Post by kellemes on 2008-01-17
> **Mats_swe said:**
> 
I thought I should try Kubuntu or something else.

That's a different story..
If you want to play with one of the **many** other distro's you don't need to uninstall Ubuntu at all.. You can simply install the other distro using the same partitions Ubuntu is on right now. Installers will simply format (if you wish) the partitions and do there thing..

---

### Post by stoodleysnow on 2008-01-17
> **kellemes said:**
> That's a different story..
If you want to play with one of the **many** other distro's you don't need to uninstall Ubuntu at all.. You can simply install the other distro using the same partitions Ubuntu is on right now. Installers will simply format (if you wish) the partitions and do there thing..

When you install a Linux distribution, such as Ubuntu, Kubuntu or whatever else you want, part of the installation process involes formatting at least part of, or all of (the choice is yours) the hard drive. If you need help formatting, just ask and somene will talk you through he installation.
:popcorn:

---

