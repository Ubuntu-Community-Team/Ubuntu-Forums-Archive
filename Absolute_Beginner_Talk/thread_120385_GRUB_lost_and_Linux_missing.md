---
title: "GRUB lost and Linux missing?"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-21
My windows partition was not working so Ibooted into Windows Recovery CD and typed fixmbr. Now grub is gone and I have no way to get it. Does anybody know how to get it from a Live CD. I've tried
[http://ubuntuforums.org/showthread.php?t=120079&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=120079&highlight=reinstall+grub)
but it doesn't work. I've also not been able to install it throught the Ubuntu Install C. I don't know what to do. My windows partion is lost, can't boot into it and my linux partition is covered somewhere in Linux. I know linux works but I just can't get to it.

If anybody has suggestion as to how to get it back, PLEASE post anything. I'll accept any advice, even if I've already tried it. 

I Just want Linux Back!

:h34r: Jaygo333 :h34r:

---

### Post by Jaygo333 on 2006-01-21
PLEASE Anybody!

I just want Linux Back. 
I have to write this in Ubuntu Live CD.
I don't hae an immediate OS.
I just want Linux Back.

:h34r: Jaygo333 :h34r:

---

### Post by ysse on 2006-01-21
Windows has overwritten your Master Boot Record (MBR). But if you have the install CD, it's easy to fix. Look at [this  Wiki page]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")

---

### Post by ubuntuuser on 2006-01-21
You could download a Live-CD, burn and boot it, then mount the drive where you installed linux on. Then open a terminal and type ```
chroot /path/to/drive /bin/bash
```. Then type ```
/sbin/grub-install
``` and reboot. It's been a while since I last did that, so maybe someone could comment on that.

---

