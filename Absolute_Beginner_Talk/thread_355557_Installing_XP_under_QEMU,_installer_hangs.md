---
title: "Installing XP under QEMU, installer hangs"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Robert Leithe on 2007-02-07
I haven't been running Ubuntu (6.10) for *that* long, but during my time away from XP there are the odd program I can't seem to get running using WINE. So I found this How-To [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) and thought I'd give it a try.

However, as mentioned in the article "However, on some systems the last part of the initial install, pictured, below, will stick around for a very long time. In this case, just reboot (restart QEmu), and the installer will proceed past this point."
As it turns out, the installer did stick around for a very long time. I quit the QEMU and restarted it using "qemu -hda windows.img -cdrom /dev/cdrom -m 256". The XP setup resumed but still seems to be lingering at this point.
Any hints, tips or suggestions as to complete my installation?

Sincerely
Robert Leithe

EDIT: It turned out I was not patient enough.
The first time I waited for almost an hour, and in all my years installing XP I've never waited that long. So (as I mentioned) I quit the QEMU and restarted it. This time, the installer did go on, but it took longer than I was prepared for - didn't time it this time but the installation is now complete.

Case closed :)

---

### Post by Medieval_Creations on 2007-02-07
I've never got XP to run quite right under QEMU & KQEMU.

I've been playing with VirtualBox in over the last few days & I really do like it.  I've gotten everything to work properly in 3 days & XP runs as well as it would if it were native.

Thread: [http://www.ubuntuforums.org/showthread.php?t=338931](http://www.ubuntuforums.org/showthread.php?t=338931)
Site: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Robert Leithe on 2007-02-07
Thanks, if I can't get QEMU to work, I'll look into this.

---

### Post by Medieval_Creations on 2007-02-07
One other thing you can try *(I had to look in my old notes)* :)

Try this at the end of your command. ```
-win2k-hack
```

Also if you are using KQEMU remove that from the end of the command on the install.  That will hopefully help.

Those are the only 2 things that I know of  you can try.  Hope they help.

---

