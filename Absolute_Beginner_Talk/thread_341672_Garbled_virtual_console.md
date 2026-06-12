---
title: "Garbled virtual console"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-01-19
Whenever I try to switch over to the virtual console (ctl+alt+1) the screen goes all multi colored and garbled, I can switch back to the GUI fine, but virt console is all wacky, this seems like it would be backwards (Im happy its not) heh. Anyone got any ideas?

---

### Post by taurus on 2007-01-19
Is it the same with <Ctrl><Alt>F2?

---

### Post by Daergeth on 2007-01-19
Yep it sure is, I tried it on all the ctl+alt F keys, odd huh :)

---

### Post by taurus on 2007-01-19
What does the entry in /boot/grub/menu.lst for **kernel** look like anyway?

Applications -> Accessories -> Terminal
```
sudo cat /boot/grub/menu.lst
```

---

### Post by Daergeth on 2007-01-19
```
title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot
```

---

### Post by taurus on 2007-01-19
And your /etc/inittab.

```
cat /etc/inittab
```

---

### Post by Daergeth on 2007-01-19
There is no inittab, just inetd.conf , init.d and initramfs-tools ;)

---

### Post by Johan! on 2007-01-19
This worked on my laptop:

(1) At the bootup menu (GRUB), select your default kernel. You may need to press ESC to see this menu.

(2) Press e for edit.

(3) Choose the first line (it should start with "kernel"). Press e again.

(4) Move to the end of the line, remove the word "splash", press enter.

(5) Press b to boot.

If this works, edit menu.lst to remove the splash option.

---

### Post by taurus on 2007-01-19
> **Daergeth said:**
> There is no inittab, just inetd.conf , init.d and initramfs-tools ;)

That's all you have in /etc!!!

```
ls /etc
```

---

### Post by Daergeth on 2007-01-19
Sorry, I have more, ALOT more, those are just the ones that have 'init' in them :)

And the editing splash at boot worked!

Thanks guys 8)

---

