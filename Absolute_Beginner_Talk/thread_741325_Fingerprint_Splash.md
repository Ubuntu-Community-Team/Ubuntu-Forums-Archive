---
title: "Fingerprint Splash"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by spyd3r on 2008-03-31
I recently installed the Fingerprint Boot Splash and the image comes up fine, but there is a black box above the load bar where there is supposed to be other stuff. Any input would be appreciated.

---

### Post by fela on 2008-03-31
you can use startup-manager to add shell output to the boot splash. Be sure to backup /boot/grub/menu.lst though before installing startup-manager, as it can muck it up.

---

### Post by spyd3r on 2008-04-02
won't removing 'quiet' from the line do the same? tried this and i still have black box.

---

### Post by atagar on 2008-05-09
The issue is that you're using the wrong screen resolution. The instructions mention that you need to add 'vga=791' to the kernel line in /etc/boot/menu.lst. In addition to this I found (for Hardy) that I needed to make the following changes:

Change the resolution in /etc/usplash.conf to 1024x768
sudo update-initramfs -u -k `uname -r`

---

