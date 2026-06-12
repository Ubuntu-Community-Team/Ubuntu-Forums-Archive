---
title: "Windows 8 in dual boot"
date: 2012-06-10
forum: Any Other OS
---

### Post by meijin3 on 2012-06-10
I've installed Ubuntu alongside Windows through a dual boot (I've partitioned my hard drive, not used Wubi). I'd like to install Windows 8 Consumer Preview over my Windows 7 installation. Will this effect Ubuntu in my other partition? I'm inclined to say no but I do want to make certain that it will be fine as it is my main OS.

---

### Post by wilee-nilee on 2012-06-10
> **meijin3 said:**
> I've installed Ubuntu alongside Windows through a dual boot (I've partitioned my hard drive, not used Wubi). I'd like to install Windows 8 Consumer Preview over my Windows 7 installation. Will this effect Ubuntu in my other partition? I'm inclined to say no but I do want to make certain that it will be fine as it is my main OS.

It will over write the mbr, you will just need to reload grub there.

---

### Post by meijin3 on 2012-06-10
> **wilee-nilee said:**
> It will over write the mbr, you will just need to reload grub there.

I'd really appreciate it if you or somebody else could give me instructions to do this :)

---

### Post by wilee-nilee on 2012-06-10
> **meijin3 said:**
> I'd really appreciate it if you or somebody else could give me instructions to do this :)

To do what?

If you mean reloading the mbr use the boot-repair tool the recommended repair, if there is problem, there is a bootinfo summary generated, save the HTTP address and post it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by meijin3 on 2012-06-10
> **wilee-nilee said:**
> To do what?

If you mean reloading the mbr use the boot-repair tool the recommended repair, if there is problem, there is a bootinfo summary generated, save the HTTP address and post it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks so much! There really should be a like button on this forum!

---

### Post by wilee-nilee on 2012-06-10
> **meijin3 said:**
> Thanks so much! There really should be a like button on this forum!

Cool it sounds like you understand the W8 install part, one never knows. ;)

---

### Post by oldfred on 2012-06-10
Downloading Boot-Repair is an easy way to repair a system. Always worth having in the repair tool box.

Also:
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

