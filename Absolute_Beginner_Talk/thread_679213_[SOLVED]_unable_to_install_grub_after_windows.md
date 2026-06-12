---
title: "[SOLVED] unable to install grub after windows"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2008-01-26
i run into the problem when i hit the second command.

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 

it's the right partition, i think that the reason is that it's up for 23 mounts check. 
i stupidly installed windows without doing that check. is there a workaround or something?

thanks
ricky

---

### Post by logos34 on 2008-01-26
you can run filesystem check from the live cd:

**sudo fsck /dev/sda1** (or whatever your ubuntu root is)

you could also use Super Grub Disk to restore grub bootloader to mbr

---

### Post by CheShA on 2008-01-26
before both these commands, try doing 
```
grub > device (hd0) /dev/sda
```

replace "sda" with the appropriate name for your drive.

---

### Post by rickycodie on 2008-01-27
super grub fixed it.

---

