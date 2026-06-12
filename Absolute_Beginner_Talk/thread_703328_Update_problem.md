---
title: "Update problem"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by personal-data-removed on 2008-02-21
I cant do updates in my system.
When i click update icon, it appears the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

I type on console: sudo dpkg --configure -a

The console does the following:

installing linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.

When i type update button again it repeats the same message error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

Or says that i have other update process open (i dont), and for me to shut it before update.

thanks in advance for help

---

### Post by personal-data-removed on 2008-02-21
After restarting the system appears the following message:

Isto significa normalmente que outra aplicação de gestão de pacotes (como o apt-get ou aptitude) está a ser executada. Feche essa aplicação em primeiro lugar.

Apt-get or aptitude is being executed, close those applications...
but i dont have those running (cant find them running in system monitor), what to do ?

---

### Post by P4oL1n0 on 2008-02-21
You probably have open Synaptic or other similar applications.. close all and try again ;)

---

### Post by personal-data-removed on 2008-02-21
"You probably have open Synaptic or other similar applications.. close all and try again"
I dont have Synaptic or similar applications opened, i only have console.

---

### Post by personal-data-removed on 2008-02-21
if i close console, and try update again, the error returns:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

---

### Post by Anicka on 2008-02-21
Run the command ```
sudo dpkg --configure -a
```and post the output.

---

### Post by P4oL1n0 on 2008-02-21
> **jocampeao said:**
> if i close console, and try update again, the error returns:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

For those packages you must type this command:
```
sudo apt-get dist-upgrade
```

---

### Post by personal-data-removed on 2008-02-21
Problem solved.

sudo dpkg --configure -a

Output:
A instalar linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
[COLOR="Red"](in last time i used the command it stoped here)[/COLOR]
User postinst hook script [/usr/sbin/update-grub] died with signal 2, without coredump
A instalar linux-headers-2.6.22-14 (2.6.22-14.52) ...
A instalar libclamav2 (0.91.2-3ubuntu2.3) ...
A instalar clamav-base (0.91.2-3ubuntu2.3) ...
A instalar libqt4-core (4.3.2-0ubuntu3.2) ...
A instalar firefox (2.0.0.12+2nobinonly+2-0ubuntu0.7.10) ...
Please restart any running Firefoxes, or you will experience problems.
A instalar libcdio6 (0.76-1ubuntu2.7.10.1) ...
A instalar linux-headers-2.6.22-14-generic (2.6.22-14.52) ...
A instalar libqt4-gui (4.3.2-0ubuntu3.2) ...
A instalar libqt4-sql (4.3.2-0ubuntu3.2) ...
A instalar clamav-freshclam (0.91.2-3ubuntu2.3) ...
A instalar firefox-gnome-support (2.0.0.12+2nobinonly+2-0ubuntu0.7.10) ...
A instalar libiso9660-4 (0.76-1ubuntu2.7.10.1) ...
A instalar clamav (0.91.2-3ubuntu2.3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

now it let me do the updates.
the strange is when i used that command before, it stoped in the middle... go figure.
Perhaps i didnt wait enough time and closed the console, but it stoped more than five minutes, there.

thanks

I also typed sudo apt-get dist-upgrade (after the updates)
and i have 0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.

thanks

---

### Post by Begemot74 on 2008-02-21
I'm also having problems updating my system (7.10) - for the past week or so, whenever i try to do so, i get an error message saying archive.ubuntu.com is uncontactable. Internet connectivity is fine otherwise. When I first installed Ubuntu, update worked fine, and I'm not aware of having made any changes that would cause this issue. Does anyone have any suggestions for me, please?

---

