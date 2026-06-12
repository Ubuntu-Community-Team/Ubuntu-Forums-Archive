---
title: "Dual boot Ubuntu and XP"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by darph_bobo on 2005-10-12
I installed Ubuntu and during setup I selected lilo to install on the mbr at least I think that's what did.
Anyhow, linux boots but I don't have boot menu to choose between XP and Linux.

Any ideas or suggestions would be welcome.

Thanks,
Darph Bobo

---

### Post by adwait on 2005-10-12
Does GRUB show up? If so you can add the Windows option to it.... To do so, open the /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```

Now find the entires for Linux kernels and after then add the following line:
```

title            Windows
root           (hd0,0)
savedefault
makedefault
chainloader +1
```

The root line is system dependant. In this case, windows is on the first partition of the first hard disk, modify according to your system.

---

### Post by wombat20 on 2005-10-12
Sometimes you don't see the GRUB or LILO boot menus unless you press ESC when booting (this is the hidemenu option) - it only flashes up for a short time to tell you, so it's easy to miss.  I think you can change the timeout for this too.

---

### Post by JakeSpeare on 2005-10-12
yes. change the timeout in the /etc/grub.conf file.  Usually set to 5 or 10 which is sometimes 'just' enough to not catch it.  Be sure to back up your grub.conf file before making changes ( sudo cp /etc/grub.conf /etc/grub.conf-bak)

Best of luck.

---

### Post by cyberdyne on 2006-07-01
[B]I have this same problem, but got a *little* further.

My current fstab file reads (#commented-out lines ommited):[/B]

#start
default 0

timeout        10

title        Ubuntu, kernel 2.6.15-25-386
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb3 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
boot

title        Other operating systems:
root

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
#end

[B]However, linux still boots as default.
Any help appreciated.
Thank you.[/B]

---

### Post by cyberdyne on 2006-07-01
I found my answer [here](http://www.ubuntuforums.org/showpost.php?p=1201235&postcount=4).
Thanks.

---

