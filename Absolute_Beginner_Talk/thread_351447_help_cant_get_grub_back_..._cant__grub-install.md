---
title: "help cant get grub back ... cant  grub-install"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-02-01
I killed my grub when i reinstalled windows.  i try grub-install /dev/hda but it doesnt work.   I tried following [http://www.ubuntuforums.org/showthre...t=restore+grub](http://www.ubuntuforums.org/showthre...t=restore+grub) but it must be dapper cuz it seems to be different.  I have no floppy drive so i cant make a boot disk.. please help!  I have to write a bash script by tomorrow

---

### Post by g3k0 on 2007-02-01
ubuntu@ubuntu:/santana/bin$ grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

---

### Post by meng on 2007-02-01
What error did you get with
grub-install /dev/hda

?

---

### Post by meng on 2007-02-02
You could try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and don't forget to use "sudo" in front of the commands.

---

### Post by rccharles on 2007-02-02
> **g3k0 said:**
> I killed my grub when i reinstalled windows.  i try grub-install /dev/hda but it doesnt work.   I tried following [http://www.ubuntuforums.org/showthre...t=restore+grub](http://www.ubuntuforums.org/showthre...t=restore+grub) but it must be dapper cuz it seems to be different.  I have no floppy drive so i cant make a boot disk.. please help!  I have to write a bash script by tomorrow

Another option, would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

Robert

---

### Post by g3k0 on 2007-02-02
That link seemed to work for me!  If i dont respond again it is because it works! thanks alot.  I'm off to reboot and cross my fingers.

---

### Post by Patrick K on 2007-02-02
I second SuperGrub. It saved my bacon.

---

### Post by rccharles on 2007-02-02
> **rccharles said:**
> Another option, would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.



superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org/?section=screenshots](http://supergrub.forjamari.linex.org/?section=screenshots)

You cursor down to the line you want.  

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.  

I wrote superGrub out to cd and it worked for me.  You can boot your partition even without grub on the partition.

..........

Another option for you would be for you to download and to use the live cd for your project.

..........

Word of advice.  Don't update your computer when you have something important to do.  Always have a backup strategy.


Robert

---

