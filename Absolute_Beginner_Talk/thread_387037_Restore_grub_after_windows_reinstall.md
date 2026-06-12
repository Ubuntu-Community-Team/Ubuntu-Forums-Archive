---
title: "Restore grub after windows reinstall?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-17
I am contimplating reinstalling XP to be able to update my bios. My motherboard went out before I installed Ubuntu/Kubuntu. When I got the computer back, I installed them both (dual boot) and did not reinstall XP. I had it updated before the motherboard went out and was able to update via cd at that point.My bios needs two updates that have to be performed in order and the first is EXE or floppy only. I do not have a floppy drive. My concern is when Windows rewrites it's master boot record to the HD, I will have to reinstall grub. Is it possible to do this and keep my grub menu lists that I already have? Currently Kubuntu's grub menu controls the boot menu since it was installed after Ubuntu. I would have to be able to use the Kubuntu menu list. This scares me since I just got the 686 smp kernels for dual processors and ATI 3D acceleration going. Anyone have any ideas or advice?

---

### Post by Atreus12 on 2007-03-17
I ran into a similar problem, and I ended up using gag [(link)](http://users.bigpond.net.au/hermanzone/p12.htm).

The way it works is that gag is in the MBR, so when you boot, the computer loads gag. Then you install grub to the partition the OS is on. This way, you can chainload from GAG to whatever operating system you are going to boot. This means that each OS can have it's own grub, and they will all update their own grub menus.

It will boot xp by default as well.

There may be a better solution, this one is working for me. I like it because you aren't dependate on any operating system to boot another operating system.

-Andrew

---

### Post by ajmorris on 2007-03-17
> **67GTA said:**
> I am contimplating reinstalling XP to be able to update my bios. My motherboard went out before I installed Ubuntu/Kubuntu. When I got the computer back, I installed them both (dual boot) and did not reinstall XP. I had it updated before the motherboard went out and was able to update via cd at that point.My bios needs two updates that have to be performed in order and the first is EXE or floppy only. I do not have a floppy drive. My concern is when Windows rewrites it's master boot record to the HD, I will have to reinstall grub. Is it possible to do this and keep my grub menu lists that I already have? Currently Kubuntu's grub menu controls the boot menu since it was installed after Ubuntu. I would have to be able to use the Kubuntu menu list. This scares me since I just got the 686 smp kernels for dual processors and ATI 3D acceleration going. Anyone have any ideas or advice?

The menu.lst file will be retained from re-installing windows. All you need to do to be able to use grub again after re-installing windows is put grub back into the MBR. You will not need to add any previous entries that were already there.

---

### Post by 67GTA on 2007-03-17
Oops

---

### Post by 67GTA on 2007-03-17
So just basically put grub on a disk and reinstall it after XP and it will automatically use my existing grub menu? I have never installed grub by it's self. How will it know which menu list to use? Ubuntu is first on the disk, will it use it by defualt, or will it look for all menu lists? My Ubuntu grub list does not have Kubuntu in it. Kubuntu has both. I guess if I made sure they both contained all boot options it wouldn't matter?

---

### Post by ajmorris on 2007-03-17
> **67GTA said:**
> So just basically put grub on a disk and reinstall it after XP and it will automatically use my existing grub menu? I have never installed grub by it's self. How will it know which menu list to use? Ubuntu is first on the disk, will it use it by defualt, or will it look for all menu lists? My Ubuntu grub list does not have Kubuntu in it. Kubuntu has both. I guess if I made sure they both contained all boot options it wouldn't matter?

It will automatically install to /boot/grub which is where the menu.lst file is. You must set the ubuntu partition (in your case hd0,0 in grub) to the root partition and re-install. If you have the ubuntu live cd then you can use that to restore grub. also i find the "grub" command to bring up the grub console is easier than the "grub-install." if you need help with the grub commands just ask. :)

---

### Post by imasickboy on 2007-03-18
This should take care of all your GRUB restoring needs:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I had just reinstalled XP, and lost access to my Ubuntu install completely. A different boot manager still would not allow me to boot into it. I restored GRUB, guided by the link above, and was successful in getting back in, as well as having my old GRUB menu intact.

---

