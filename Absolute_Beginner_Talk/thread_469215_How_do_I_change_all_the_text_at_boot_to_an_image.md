---
title: "How do I change all the text at boot to an image"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-06-09
I installed KDE core and I got a nice grub boot image and a nice splash screen but in between there's all the text going by. I know its possible to configure that  I just don't know what it's called or how to configure it. Thanks.

---

### Post by Portable_Jim on 2007-06-09
I have heared it it called silent boot - on the bios anyway, don't know about Ubuntu.

---

### Post by RomeReactor on 2007-06-09
Hi. Looks like you may have disabled quiet splash from grub. Enter this in Konsole:
```
cat /boot/grub/menu.lst
```
scroll down to the end of the file and see if **quiet** appears there, like this:
```
title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
**quiet**

### END DEBIAN AUTOMAGIC KERNELS LIST
```
If not, then:
```
kdesu kate /boot/grub/menu.lst
```
and add it below the kernel entry like in the example. Save the file, close and reboot.

**NOTE:** Don't change anything else in the file.

---

### Post by thelocust on 2007-06-09
This is my menu.list entry. It was already set to quiet.

```
title        Kubuntu
root        (hd0,0)
kernel        /vmlinuz-2.6.20-16-generic root=UUID=f27ad5b3-644a-41d0-96db-9b29566eaf2a ro quiet splash
initrd        /initrd.img-2.6.20-16-generic
quiet
savedefault
```I've been looking around and I think its called the bootsplash.

---

### Post by thelocust on 2007-06-09
Thanks for the help I figured it out I'm gonna go with a program named [splashy.]("http://ubuntuforums.org/showthread.php?t=216597&highlight=splashy")

---

