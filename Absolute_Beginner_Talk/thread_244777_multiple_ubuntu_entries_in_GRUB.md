---
title: "multiple ubuntu entries in GRUB"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by camelgrass on 2006-08-26
I recently reinstalled Ubuntu 6.06 but now have 2 entries for Ubuntu in GRUB. How do I remove the multiple entry?

Thank you, Marty

---

### Post by jordanmthomas on 2006-08-26
If one is for recovery mode, you *may* want to keep it.

Either way, you can go to a terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

Find what you want to remove and do so.  Mine looks like this:

```
title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash vga=7
92
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

[COLOR="Red"]title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro single vga=792
initrd          /boot/initrd.img-2.6.15-26-686
boot[/COLOR]

```

If I wanted to get rid of the second one, I'd delete (or comment out) the entry I wanted gone. (I put this in red)

Hope this helps

---

### Post by confused57 on 2006-08-26
I think you should definitely keep the option to bootup into recovery mode, learn some basic commands and access to some important configuration files, using **sudo nano**:

e.g.
/etc/apt/sources.list
/boot/grub/menu.lst
/etc/X11/xorg.conf
dpkg-reconfigure xserver-xorg(don't use nano with this)

etc.

in case you have problems booting in the GUI, you may be able to reconfigure your system to enable you to.

---

### Post by aysiu on 2006-08-26
I second jordanmthomas' recommendation that you keep recovery mode in there, unless by "two entries" you mean that there are actually four entries--two for each of two kernel versions.

If you do get rid of recovery mode, make sure you at least have a Ubuntu or Knoppix live CD handy.

---

### Post by camelgrass on 2006-08-27
> **aysiu said:**
> I second jordanmthomas' recommendation that you keep recovery mode in there, unless by "two entries" you mean that there are actually four entries--two for each of two kernel versions.

If you do get rid of recovery mode, make sure you at least have a Ubuntu or Knoppix live CD handy.

Yep there are actually 4 entries and 2 kernel versions. Why is that? Was there a very recent kernel update? I reinstalled from the same Ubuntu 6.06 CD and I thought I had all updates on the original installation.

I will keep recovery mode in GRUB because I need it now! I can enter recovery mode but how do I use the help menu at the bottom; eg. "^X"?

I stuffed up the xorg.conf earlier trying to fix a video driver problem and now Xserver won't load.

I know how to open xorg.conf in recovery mode but I have no idea about the commands to save etc. What's this symbol mean in help menu "^"?.

Sorry, I tried to google it but could not find an answer. Also is there a command update the xorg.conf file to the original one?

Thanks for your trouble, Marty

---

### Post by aysiu on 2006-08-27
If you're editing with *nano* then you save with Control-X, Y, and Enter (in that order).

```
nano -B /etc/X11/xorg.conf
``` allows you to edit the xorg.conf file *and* back it up at the same time.

Reboot by typing ```
reboot
```

You can uninstall the older kernel with Synaptic or Adept and searching for *linux-image*.

---

