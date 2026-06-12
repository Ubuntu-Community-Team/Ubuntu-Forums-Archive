---
title: "Dual boot with Mandriva Spring 2007"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-09-13
hello i want to dual boot ubuntu and Mandriva, here is what i have in my menu.lst:

title           Mandriva Spring 2007
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/hda3 root
savedefault

but it sends me an error, i think my problem is here:

 /boot/vmlinuz-2.6.20-15-generic root=/dev/hda3 

but i dont know 

here is my fdisk -l

Disk /dev/sda: 60.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1424    11438248+   7  HPFS/NTFS
/dev/sda2            1425        6713    42483891+  83  Linux
/dev/sda3            6714        8414    13663282+  83  Linux

i want to boot /dev/sda3 ... that one is Mandriva, 

thank you :)

---

### Post by Happy_Man on 2007-09-13
Uh.... if this is your first/only HDD, shouldn't that be "root (0,0)" instead of "root (0,2)"?

---

### Post by Pabx on 2007-09-13
> **Happy_Man said:**
> Uh.... if this is your first/only HDD, shouldn't that be "root (0,0)" instead of "root (0,2)"?

Nop thats the partition, like i wrote i think my error is here:
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/hda3 root

thank you for you thelp

---

### Post by Happy_Man on 2007-09-13
*slaps self* right, I'm sorry. My brain's on the fritz today. Why do you have "root" after the kernel line?

---

### Post by Pabx on 2007-09-13
> **Happy_Man said:**
> *slaps self* right, I'm sorry. My brain's on the fritz today. Why do you have "root" after the kernel line?

Dont know a friend told me to put it that way .... but there is an error...

---

### Post by Happy_Man on 2007-09-13
Try booting with the "root" gone. You have already specifed root with "root=/dev/sda3", so the other root is probably tripping it up.

---

### Post by logos34 on 2007-09-13
you might try:

> title Mandriva Spring 2007
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/**[COLOR="Red"]s[/COLOR]**da3
[COLOR="Red"]initrd /boot/initrd.img-2.6.20-15-generic[/COLOR]
savedefault
boot

---

### Post by Pabx on 2007-09-13
> **Happy_Man said:**
> Try booting with the "root" gone. You have already specifed root with "root=/dev/sda3", so the other root is probably tripping it up.

Nop it does not work... :confused:

---

### Post by Pabx on 2007-09-13
> **logos34 said:**
> you might try:

No, when i try to boot it gives me an error:

Error 15:

file not found :confused: :confused: :confused:

---

### Post by logos34 on 2007-09-13
is your mandriva partition (sda3) mounted and what does the boot folder show?

---

### Post by Pabx on 2007-09-13
> **logos34 said:**
> is your mandriva partition (sda3) mounted and what does the boot folder show?

Yep its mounted and the boot folder shows: 

grub
config
initrd.img and another files...

---

### Post by Pabx on 2007-09-13
What can i do?!?!? :confused:

---

### Post by logos34 on 2007-09-13
Just 'initrd.img', no ending '-<kernel>-generic'? what about vmlinuz?  Because the kernel and initrd lines in menu.lst need to match how they're listed in the Mandriva boot.  So just use 'vmlinuz' and 'initrd.img' if that's what they're named in the boot dir.  

For reference, here's an actual menu.lst from a Mandriva install.  Maybe it will help you adapt you own Mandriva entry in your ubuntu grub menu.lst so it boots.

> title Mandriva Spring 2007
kernel (hd1,6)/boot/vmlinuz 
BOOT_IMAGE=Mandriva_Spring_2007 root=/dev/hdb7
resume=/dev/hdb6 splash=silent vga=788
initrd (hd1,6)/boot/initrd.img

add:
here's another

title Mandriva
kernel (hd1,1)/boot/vmlinuz-2.6.17-14mdv BOOT_IMAGE=Mandriva root=/dev/hdb2 resume=/dev/hdb1 splash=verbose vga=788
initrd (hd1,1)/boot/initrd-2.6.17-14mdv.img

note: 'resume' is swap

---

### Post by Pabx on 2007-09-13
i attached an image with all contents

---

### Post by Pabx on 2007-09-13
nop it does not work...

---

### Post by angryfirelord on 2007-09-13
Re-install Ubuntu. It'll replace Mandriva's grub with Ubuntu's grub & Ubuntu is a lot better at picking up other distros.

---

### Post by Pabx on 2007-09-13
> **angryfirelord said:**
> Re-install Ubuntu. It'll replace Mandriva's grub with Ubuntu's grub & Ubuntu is a lot better at picking up other distros.

No way... i have my ubuntu very fine and i cant download again all the things...

---

### Post by Pabx on 2007-09-13
> **Pabx said:**
> No way... i have my ubuntu very fine and i cant download again all the things...

Dont worry anymore, it would end like this:

title Mandriva Spring 2007
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-13mdv root=/dev/hda3
savedefault
boot

Thank you for helping

---

### Post by logos34 on 2007-09-13
there is one more way--have grub entry merely point to the Mandriva menu.lst (or whatever it's called). 

> title Mandriva Spring 2007
configfile (hd0,2)/boot/grub/menu.lst

---

