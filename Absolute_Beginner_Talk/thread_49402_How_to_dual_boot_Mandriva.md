---
title: "How to dual boot Mandriva"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by davidgypsy on 2005-07-16
.

---

### Post by Seti on 2005-07-16
Maybe try to reinstall GRUB from your Ubuntu partition? I'm just guessing, I've never had to do this.

---

### Post by aysiu on 2005-07-16
Theoretically, installing Mandriva's Grub to root instead of MBR, then copying the Mandriva entry from Mandriva's /boot/grub/menu.lst to Ubuntu's /boot/grub/menu.lst should work.

I just did it, but I got some weird errors when Mandriva was booting up--something about some files being read-only. I ended up at a log-in prompt and couldn't startx as user or root.

---

### Post by snds24 on 2005-07-16
If Ubuntu bootloader (GRUB) is in MBR

Try to add this to your Ubuntu /boot/grub/menu.lst

title Mandriva at hda5
rootnoverify (hd0,4)
chainloader +1

This is mine:

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1
gfxmenu /boot/grub/message

title MEPIS at hda5, kernel 2.6.10
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,4)/boot/initrd.splash 

title Windows at hda1
rootnoverify (hd0,0)
chainloader +1

title Debian at hda3
rootnoverify (hd0,2)
chainloader +1

title MEMTEST
kernel /boot/memtest86.bin

---

### Post by davidgypsy on 2005-07-16
[QUOTE=snds24]If Ubuntu bootloader (GRUB) is in MBR

Try to add this to your Ubuntu /boot/grub/menu.lst

title Mandriva at hda5
rootnoverify (hd0,4)
chainloader +1

This is mine:

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1
gfxmenu /boot/grub/message

[/QUOTE]

Worked great!! Thanks, and now I have some pretty colours in Grub too! ;-)

---

### Post by eeried on 2005-08-02
Isn't chainloader for Windows OS only?

---

### Post by Jenda on 2005-08-04
Hello, world... I've been around, but now I'm back and on Ubuntu. Except... I installed Mandrake, and it gobbled up the MBR with its own GRUB. Can anyone tell me what command GRUB needs to boot up my beautiful brand new Ubuntu (Hoary)? I know the partition it's on, I just can't boot it. Thanks.

---

