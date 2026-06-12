---
title: "[SOLVED] Is A Plain Black Boot Screen Normal In Gutsy Beta?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Anthony M on 2007-10-10
I've been running the beta for a week or so, (Dual boot w/ XP) and everytime I boot, after selecting Ubuntu from the Grub menu, the screen goes black up until the login screen.

When I was running the livecd there was a nice Ubuntu boot screen with a progress bar. Now its just black...

Sorry if this has been asked before, I couldn't find any specifics.

Thanks!

---

### Post by Bliepo32 on 2007-10-10
Do the Caps Lock and the Scroll lock light on your keyboard flash (just out of curiosity)?

---

### Post by Anthony M on 2007-10-10
AFAIK, they dont flash. The num lock comes on once Gnome loads. Everything works fine other than having no boot screen.

I thought I read somewhere that this may be normal in a dual boot system with Gutsy :confused:

---

### Post by Martje_001 on 2007-10-10
Can we see the output of 'cat /boot/grub/menu.lst'?

---

### Post by Anthony M on 2007-10-10
Here is the content of menu.lst. I have removed the 'quiet' from the first Ubuntu entry, but all that gives me is a split second of text during the boot up. I have installed usplash-switcher to try to get a boot screen but that seemed to have no effect.

For the record, this is on a Dell Dimension 2400 with onboard Intel Graphics.

EDIT: I just noticed the there is "quiet" in the words running down the left column, should I  remove that as well?

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=41f38eda-b34a-4eca-898e-3ab6cd0ce809 ro splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=41f38eda-b34a-4eca-898e-3ab6cd0ce809 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows NT/2000/XP
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by Anthony M on 2007-10-11
*shameless bump*

Anybody?

---

### Post by Circus-Killer on 2007-10-11
no, dont remove the word 'quiet'.

that quiet is to specify that when the boot screen shows, that you dont want the scrolling text to display, just the image.

unfortunetly, i have no idea why your boot screen is not showing.
(i dont dual boot, but on my gutsy install i see the boot screen fine)

---

### Post by shae on 2007-10-11
Try

```
sudo dpkg-reconfigure usplash
```

---

### Post by Anthony M on 2007-11-01
Finally solved this problem....

I edited my /boot/grub/menu.lst to include vga=normal. Otherwise I get a unspecified video error at boot. 

I then edited my /etc/usplash.conf to x=640 y=480

I now have a kick butt Ubuntu boot screen!

---

