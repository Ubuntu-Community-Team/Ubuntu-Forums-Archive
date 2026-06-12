---
title: "i deleted the grub folder"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by radiantarchon on 2008-01-15
i actually pushed delete. which bypasses the trash. it was in my boot folder.
how do i rebuild it without restarting the computer?

---

### Post by GavinZac on 2008-01-15
sudo apt-get reinstall grub?

---

### Post by LaRoza on 2008-01-15
> **radiantarchon said:**
> i actually pushed delete. which bypasses the trash. it was in my boot folder.
how do i rebuild it without restarting the computer?

That is impossible to do, unless you are running something as root. Be careful next time.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by radiantarchon on 2008-01-15
reinstall is invalid command

---

### Post by 3rdalbum on 2008-01-15
```
sudo apt-get remove --purge grub
sudo apt-get install grub
```

I guess that would work?

---

### Post by radiantarchon on 2008-01-15
the link 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
 does not work because "find /boot/grub/stage1" requires a grub folder to be on the computer

---

### Post by GavinZac on 2008-01-15
> **radiantarchon said:**
> reinstall is invalid command
I was paraphrasing, just reinstall grub like so:
> **3rdalbum said:**
> ```
sudo apt-get remove --purge grub
sudo apt-get install grub
```

---

### Post by sumguy231 on 2008-01-15
There's the grub-install command, but I haven't used it and I don't know if you can use it on a mounted partition. Read the manpage for more details.

---

### Post by GavinZac on 2008-01-15
> **sumguy231 said:**
> There's the grub-install command, but I haven't used it and I don't know if you can use it on a mounted partition. Read the manpage for more details.

I suppose he could use a liveCD and chroot?

or maybe use Super Grub, that will repair grub, wont it?

---

### Post by JoshuaRL on 2008-01-15
Yep it will.

> **c0met said:**
> Hi FernieBiker

Before getting into the code and stuff, it might be easiest if you downloaded a bootable ISO for the program called SuperGrub. Burn this to a CD and then boot your system from this CD. It will give you options for...
[LIST]
[*]making your win(dows) drive bootable
[*]making your linux drive bootable
[*]setting your system up for a dual boot
[/LIST]
If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. You can download the ISO from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

That's from [http://ubuntuforums.org/showthread.php?t=666838](http://ubuntuforums.org/showthread.php?t=666838)  page 2.  In the end it fixed it for him.

---

### Post by mikewhatever on 2008-01-16
> **radiantarchon said:**
> i actually pushed delete. which bypasses the trash. it was in my boot folder.
how do i rebuild it without restarting the computer?

Good example as to why one should not be running as root.

---

