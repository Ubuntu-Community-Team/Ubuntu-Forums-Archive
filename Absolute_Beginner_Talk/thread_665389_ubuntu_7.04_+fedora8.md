---
title: "ubuntu 7.04 +fedora8"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by xaocan on 2008-01-12
I've installed fedora 8 today and i got into a little problem. On 1 partition i got fedora and on other ubuntu 7.04 and i got no idea how can i log into ubuntu(when i turn on my pc it logs into fedora). Plz help me (lol).

---

### Post by Kingsley on 2008-01-12
Press a key when GRUB is loading. Afterwards, you should see a menu allowing you to choose Fedora or Ubuntu.

---

### Post by LinuxGuy1234 on 2008-01-12
> **xaocan said:**
> I've installed fedora 8 today and i got into a little problem. On 1 partition i got fedora and on other ubuntu 7.04 and i got no idea how can i log into ubuntu(when i turn on my pc it logs into fedora). Plz help me (lol).

Press any key and see a entry for Ubuntu. If not, use these GRUB commands (replace hd0,0 with the GRUB notation for / or /boot and /dev/hda1 with the LInux name of your Ubuntu partition):
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
boot

---

### Post by xaocan on 2008-01-12
what should i write in grub?

---

### Post by LinuxGuy1234 on 2008-02-09
> **xaocan said:**
> what should i write in grub?
What I mean is:
Boot the computer.
Press any key.
Press c.
Then do these commands:
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
boot

---

