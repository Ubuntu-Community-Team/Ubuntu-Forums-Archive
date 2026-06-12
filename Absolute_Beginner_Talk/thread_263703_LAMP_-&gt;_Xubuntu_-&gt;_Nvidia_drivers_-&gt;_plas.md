---
title: "LAMP -&gt; Xubuntu -&gt; Nvidia drivers -&gt; plasma TV"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by jonnythan on 2006-09-23
Here is what I've done:

Install LAMP server (install and configure vsftpd, ssh, samba, I have CLI server stuff down, I've been doing it on BSD for years).

So I want to turn this LAMP server into a DVD player.

sudo apt-get install xubuntu-desktop

Reboot into XFCE.

sudo apt-get install nvidia-glx

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nvidia-xconfig

Reboot.. kernel panic. "not syncing: VFS: Unable to mount root fs on unknown-block(8,1)"

Wipe the root partition and start over.

sudo apt-get install xubuntu-desktop

Reboot into XFCE.

Install Automatix and fire it up. Use it to install AUD-DVD, multimedia applications, and Nvidia drivers.

Reboot... kernel panic.

WTF am I doing wrong?

What am I supposed to do to get this to work? I just want to install the Nvidia drivers and, if possible, set the desktop to a resolution of 1366x768. How do I do this?

---

