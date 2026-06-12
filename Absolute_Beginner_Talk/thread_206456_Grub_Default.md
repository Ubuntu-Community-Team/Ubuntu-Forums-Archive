---
title: "Grub Default"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by thepocketdrummer on 2006-06-30
How do I make my default OS Windows in stead of Linux?

---

### Post by Ctrl+Alt+Del on 2006-06-30
sudo nano -w /boot/grub/menu.lst
and edit the num value to your needs. 
```
# default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0
```

---

### Post by thepocketdrummer on 2006-07-01
so in order to make windows my primary I would have to add

default    0

to the windows part? What do I do with the defaultsave?

---

### Post by Herman on 2006-07-01
> so in order to make windows my primary I would have to add
default    0
to the windows part? What do I do with the defaultsave?
No, here's how I do it (illustrated) [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")
Let me know if that explanation is clear enough, I still improving it.
Regards, Herman

---

### Post by thepocketdrummer on 2006-07-01
So... what would I change here?

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Stone123 on 2006-07-01
I allways use cheat on this one. I just uncomment lines in exemple for windows and its allways first there. It s never bothered buy update-grub or grub-install.
> 
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
title        Windows Whatever
root        (hd0,0)
makeactive
chainloader    +1
#




---

### Post by Herman on 2006-07-01
```
           # WARNING: If you are using dmraid do not change this entry to 'saved' or your
          # array will desync and will not let you boot your system.
          default        4
                
          splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz
                
          ## timeout sec
          # Set a timeout, in SEC seconds, before automatically booting the default entry
``` You should change it to 4.

Counting down from the top, beginning with 0, Ubuntu is 0, Ubuntu recovery is 1, memtest is 2, other operating systems is 3, and Windows is 4.

Regards, Herman. :D

---

### Post by Lord Illidan on 2006-07-01
[quote=Stone123]I allways use cheat on this one. I just uncomment lines in exemple for windows and its allways first there. It s never bothered buy update-grub or grub-install.[/quote]

Good suggestion also.

---

### Post by cyberdyne on 2006-07-01
[QUOTE=Herman]No, here's how I do it (illustrated) [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")
Let me know if that explanation is clear enough, I still improving it.
Regards, Herman[/QUOTE]


[B]Perfectly clear to me.
I couldnt find this simple, but elusive piece of info anywhere else.

Thank you!![/B]

---

### Post by thepocketdrummer on 2006-07-01
> You should change it to 4.

Counting down from the top, beginning with 0, Ubuntu is 0, Ubuntu recovery is 1, memtest is 2, other operating systems is 3, and Windows is 4.

Regards, Herman. 

THANKS! That was super easy. I didn't even notice that at the top, lol.

---

### Post by Herman on 2006-07-01
Well thank you very much too, thepocketdrummer, because with the help of your feedback I was able to edit that part of the site a couple of times and improve it so that other people should be able to understand it better now, I hope.

And cyberdyne, thank you for your feedback too, it all helps! I'm happy if people will find things in Ubuntu and GRUB easy to use.

All the best to both of you, Regards, Herman :D

---

### Post by Sean-Michael on 2006-07-03
Thankyou for the tip Stone123, 
I've been wanting to do this for quite some time now and like the way you do it'  Now to uninstall my old kernels I guess :)
Thanks'

---

