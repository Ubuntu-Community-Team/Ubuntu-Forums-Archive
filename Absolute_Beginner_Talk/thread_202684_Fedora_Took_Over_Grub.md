---
title: "Fedora Took Over Grub"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Jayzilla on 2006-06-23
Oh man.  Just for sh*ts and giggles I thought I'd install Fedora Core 5 on another partition.  MISTAKE.

Apparently it installed a new version of GRUB, which doesn't see Ubuntu.  I know it's still there, because I didn't format the partition it's on...I just can't get to it.  Any ideas?

---

### Post by nitricacid on 2006-06-23
There is a way to install just GRUB and I had seen a post about this a few days ago but didn't read the entire post.
You could try finding that post or just sit tight and let the experts reply. 
Sorry I couldn't help any further.

---

### Post by scxtt on 2006-06-23
what hard disk / partition is ubuntu on? -- you can edit grub's (grub.conf in fedora, i think) config file for fedora and add an entry for ubuntu ...

---

### Post by Apple 101 on 2006-06-23
To install GRUB:
grub-install /dev/hda

Open your Fedora grub.conf (or menu.lst) and insert the following lines:

> title "whatever you want to call your new distro"
        root (hd#,#)
        kernel /boot/vmlinuz"Your Kernel Number" ro root=LABEL=/
        initrd /boot/initrd"Your Kernel Number".img

---

