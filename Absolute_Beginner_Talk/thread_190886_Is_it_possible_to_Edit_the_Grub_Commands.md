---
title: "Is it possible to Edit the Grub Commands?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by truth on 2006-06-06
I am aware that i may edit the Grub Commands, but what i mean to say is may i remove some commands from the List!?

All i want to appear is something like this

Boot:
[Windows XP]
[Ubuntu]

Booting in 0 sec's

and just be able to only select between the two OS's. 

My dad uses my computer sometimes so i had to keep Windows XP on here, I wanted to just Have Ubuntu as my Defualt and Only OS but  o well. I thought if i could edit the Grub and have Windows boot First and Maybe even edit the Time Out to Boot thingy it would work out great!!

Any idea? 

Thx

---

### Post by painterboy on 2006-06-06
here this should help [https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS]("https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS")

---

### Post by uzi09 on 2006-06-06
you can edit the menu list from:
/boot/grub/menu.lst
please make a copy of this first so you have a backup:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

```

then you can edit it:
```

sudo gedit /boot/grub/menu.lst

```

scroll down to this section (near the end):
```


## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-22-686
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-22-686 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-686 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-22-686 root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.15-22-686
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

and you can comment out the "ubuntus" in the middle that are for recovery mode. sometimes these are helpful to have, but you can always boot with a live cd and change the settings around.

(FYI: # in front of a line comments it out)

---

### Post by truth on 2006-06-06
WOW!!! Awsome!! Thx alot guys!! this is a huge help!! Ill give it a Go right NOW!! Thx Again   =)

---

