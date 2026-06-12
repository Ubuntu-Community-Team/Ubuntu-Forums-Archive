---
title: "Question:NTFS drive"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by shushustrum on 2007-07-25
Hi im new in linux and I have an external NTFS formated hard drive.
i can see whats on it but when i try to write to it it says:"you dont have permission to write to this folder"
i try looking up what i could do and i saw something called "ntfs-3g" but don't know how to use it at all even how to enter it.
so if someone could please tell me how i could write to my ntfs external hard drive step by step directions.
thank you.

---

### Post by wolfen69 on 2007-07-25
```
sudo apt-get install ntfs-3g ntfs-config
```
ntfs-config will be in system tools

---

### Post by shushustrum on 2007-07-25
i tryed ntfs config and i checked the external hard drive box but it still didn't work.
that's way i asked step by step what to do.

---

### Post by threeonethree on 2007-07-25
first install the ntfs 3g tool from that command given above. then go to system tools > ntfs config tool and enable support for external as well as internal drives if u want..

RESTART your computer.

if it doesnt work , then boot into winblows if u have duel boot and right click on ur drives and click properties.. scan your disk for errors and click automatically fix file system option.. reboot into ubuntu and it should work

---

### Post by stchman on 2007-07-25
> **shushustrum said:**
> Hi im new in linux and I have an external NTFS formated hard drive.
i can see whats on it but when i try to write to it it says:"you dont have permission to write to this folder"
i try looking up what i could do and i saw something called "ntfs-3g" but don't know how to use it at all even how to enter it.
so if someone could please tell me how i could write to my ntfs external hard drive step by step directions.
thank you.

My recommendation is to copy all the data off that external hdd (if you have room) and convert it to FAT32.  FAT32 is a far better file system for external devices.  It is way better for devices that you intent to share among Linux and Windows.  Both Linux and Windows can read/write to FAT32 natively.

---

### Post by stchman on 2007-07-25
> **wolfen69 said:**
> ```
sudo apt-get install ntfs-3g ntfs-config
```
ntfs-config will be in system tools

You don't need to install ntfs-3g when you install ntfs-config, ntfs-config has ntfs-3g as a dependency.

---

### Post by marco123 on 2007-07-25
once you have installed ntfs3g and rebooted type   "sudo chown  yourname /media/diskname"

that should do it

---

