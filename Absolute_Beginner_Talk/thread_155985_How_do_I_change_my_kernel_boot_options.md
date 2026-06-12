---
title: "How do I change my kernel boot options"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by davidU on 2006-04-06
I have a problem with my laptop battery/power status indicator i Ubuntu 5.04, running Hoary.

I read a post by Crayoneater who fixed this problem by changing the kernal boot options for the acpi to,

acpi_os_name=Microsoft Windows 2000.

Can someone please tell me how to do this ?

regards 
DavidU:-k

---

### Post by waster on 2006-04-06
edit /boot/grub/menu.lst
Find the first section which looks like:
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.12-10-k7
savedefault
boot


add your extra bit at the end of the row starting with "kernel"

---

### Post by davidU on 2006-04-06
[QUOTE=waster]edit /boot/grub/menu.lst
Find the first section which looks like:
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.12-10-k7
savedefault
boot


add your extra bit at the end of the row starting with "kernel"[/QUOTE]

Thanks for the reply, but I am pretty new to this game and need a bit more direction.

I'm using Hoary Ubuntu 5.04.

I have two terminals.

Do I use the Root Terminal for this job ?

And, what do I do when I get there ? Please !:-|

---

### Post by meborc on 2006-04-06
well... you can go about like this...

open the terminal (normal one) and type:
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup **
that will make a backup of this file... then type:

**sudo gedit /boot/grub/menu.lst**
text editor will open and you can edit this file... BUT be careful, if you mess smth up you are a goner!

find this line (there might be many these lines... chose the first section - the newest kernel)
**[COLOR="DarkRed"]kernel /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash[/COLOR]**

and make it look like this:
**[COLOR="darkred"]kernel /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash acpi_os_name=Microsoft Windows 2000[/COLOR]**

then save and restart...

IF something goes wrong (it probably does) then boot into recovery mode and type (after login):
**sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst**

---

### Post by mdmarmer on 2006-04-06
Actually like this

kernel /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash acpi_os_name="Microsoft Windows 2000"

;-)

Mike

---

### Post by davidU on 2006-04-06
[QUOTE=meborc]well... you can go about like this...

open the terminal (normal one) and type:
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup **
that will make a backup of this file... then type:

**sudo gedit /boot/grub/menu.lst**
text editor will open and you can edit this file... BUT be careful, if you mess smth up you are a goner!

find this line (there might be many these lines... chose the first section - the newest kernel)
**[COLOR="DarkRed"]kernel /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash[/COLOR]**

and make it look like this:
**[COLOR="darkred"]kernel /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash acpi_os_name=Microsoft Windows 2000[/COLOR]**

then save and restart...

IF something goes wrong (it probably does) then boot into recovery mode and type (after login):
**sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst**[/QUOTE]

Thanks Meborc,
  I heed your words of warning, especially as I have one of those magnetic personalities which attracts those kind of errors which normal people never experience.

I'll get to it just as soon as I've finished chauffering the kids.
regards

DavidU:)

---

### Post by davidU on 2006-04-06
[QUOTE=mdmarmer]Actually like this

kernel /vmlinuz-2.6.12-10-k7 root=/dev/mapper/Ubuntu-root ro quiet splash acpi_os_name="Microsoft Windows 2000"

;-)

Mike[/QUOTE]
 Thanks mdmarmer.

I'll report back on the outcome.

regards

DavidU:)

---

### Post by az on 2006-04-06
You should really edit the 
##noaltoptions
line since the next time that your kernel is updated, it will rewrite the menu-list file and your changes will be gone.  Putting that option in the noaltoptions will result in them being passed to every linux kernel boot line when it recreates the menu.list using update-grub.

---

