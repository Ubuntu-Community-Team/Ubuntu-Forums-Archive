---
title: "Want to go from WinXP to Ubuntu, but what if..."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by nietsloh on 2007-06-09
I have a Dell laptop that I've run the Ubuntu disc on, with success. I'd like to take the "next step" and create a dual-boot system. But what if I get Ubuntu installed and change my mind -- how do I reclaim that HD space for Windows? (Yes, I know you're thinking, "Why would you want to do that?")

---

### Post by init1 on 2007-06-09
> **nietsloh said:**
> I have a Dell laptop that I've run the Ubuntu disc on, with success. I'd like to take the "next step" and create a dual-boot system. But what if I get Ubuntu installed and change my mind -- how do I reclaim that HD space for Windows? (Yes, I know you're thinking, "Why would you want to do that?")
You can delete the Ubuntu partition and resize you windows partition so that it fills the space.

---

### Post by Rocket2DMn on 2007-06-09
What about the boot loader, won't that disappear with Ubuntu?

---

### Post by Jimmyfj on 2007-06-09
Correct - WHY would you ever want to go back to Windows XP ?

As far as I know installing Ubuntu on a dual boot you'd have to consider your bootloader. GRUB is installed last if Windows is already installed, and GRUB will take over the boot from the Win-boot-loader. Moving, or deleting Ubuntu would also mean deleting GRUB and BAMM away goes everything on the drive. The way I understand GRUB it means that you'd have to reinstall your Win-box all over.

---

### Post by Wynne G Oldman on 2007-06-09
If you install Ubuntu with the wubi installer, it dosn't alter your partitions, and Windows just sees it as a program. You can dual boot, and if you get fed up with all the problems that Ubuntu has, you can simply uninstall it by removing it via "add remove programs" in control panel, and your PC will be back to how it was before you installed Ubuntu.

---

### Post by machoo02 on 2007-06-09
> **Jimmyfj said:**
> 
Moving, or deleting Ubuntu would also mean deleting GRUB and BAMM away goes everything on the drive. The way I understand GRUB it means that you'd have to reinstall your Win-box all over.This is not true.  GRUB is installed to the Master Boot Record (MBR), which is separate from Ubuntu's root partition.  If you decided to delete Ubuntu and use Windows only, you would still have GRUB on your machine.  If you wanted to get rid of GRUB, you would need to use your windows install disk and boot to a recovery shell, and use the "fixmbr" command to overwrite GRUB replace the NT bootloader

---

### Post by Wynne G Oldman on 2007-06-09
> **Jimmyfj said:**
> Correct - WHY would you ever want to go back to Windows XP ?

Because it works?

---

