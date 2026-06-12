---
title: "Make windows start up first"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by NStoker on 2008-02-05
How do i make it so M$ starts up first. I would like it so that it jsut starts M$ instead of ubuntu.  what should i do??

Thanks!

---

### Post by jordanmthomas on 2008-02-05
In Ubuntu, open up /boot/grub/menu.lst in gedit
```
gedit /boot/grub/menu.lst
```
Post what's there and we can help.

Essentially, you need to change the line
```
default 0
```
to another number (the one that corresponds to your Windows entry in GRUB)

edit
Also, are you actually using Ubuntu 4.10 or did you just put that there for fun?

---

### Post by NStoker on 2008-02-05
I'm using 7.10

edit: when i type that grub command  i get a long page of stuff. what do u want?

---

### Post by NStoker on 2008-02-05
o i usely just calll microsoft MS and I saw the $ sign. so I'm using xp,
Could u also explain things EXTREMELY simple?? I'm a big newb at ubuntu. Thanks!

---

### Post by jordanmthomas on 2008-02-05
I'd like the whole file if possible, but really all I need is to know how many items you have in your menu.lst
When you boot your computer and have the list of OSs to boot from:
```
Ubuntu 
Ubuntu recovery
Other OS
Windows
```
Something like that.  If that's what your menu looked like, you'd want to change the default to 3.
When you go to edit the file, you'll need to do
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by NStoker on 2008-02-05
I know this is overdoing it but I don't really know what u want,  That is exactly what the startup menu look like.
this is what's in that file:

# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d8d3596-0223-4b10-82ad-e5d5e690a393 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d8d3596-0223-4b10-82ad-e5d5e690a393 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by jordanmthomas on 2008-02-05
OK, 
```
gksudo gedit /boot/grub/menu.lst
```
At the very top add a line that says
```
 default 4
```
When you reboot, Windows should be the default.

Do you see how it works?
0:  Ubuntu 7.10, kernel 2.6.22-14-generic
1:  Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
2:  Ubuntu 7.10, memtest86+
3:  Other operating systems:
4:  Microsoft Windows XP Professional

---

### Post by NStoker on 2008-02-05
so it should look like this then?


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

edit:

Don't know why all those smiles are in their

---

### Post by jordanmthomas on 2008-02-05
Yes, it should look like that.
The smilies come because there's an 8 and then an )  8)

---

### Post by asmoore82 on 2008-02-05
right file, but ...

1. you need to edit it with "Admin" privilege and

2. I do _not_ recommend changing the ``default'' value,
Instead, I would cut and paste the windows boot stanza so that it is the first in the list

...

0. **_[COLOR="Red"][SIZE="4"]ALWAYS[/SIZE][/COLOR]_** make a **[COLOR="Red"]backup copy[/COLOR]** of important system files **[COLOR="Red"]before[/COLOR]** editing them!!
In a terminal("Applications -> Accessories -> Terminal"), Run:
```
sudo cp /boot/grub/menu.lst /root/grub_menu.lst
```
(that last bit is lowercase ``LST'')

1. In that same terminal Run:
```
gksu gedit /boot/grub/menu.lst
```
(that last bit is lowercase ``LST'')

2. in Gedit, Click "View -> Highlight Mode -> Scripts -> sh"

3. near the end of the file, **cut** the windows boot stanza that looks something like this:
```
title Windoze XP Professhional
rootnoverify (hd?)
chainloader +1
```

4. **paste** that stuff immediately before the "BEGIN AUTOMAGIC" line in blue...
```
[COLOR="Blue"]#
# Put static boot stanzas **before** and/or after AUTOMAGIC KERNEL LIST[/COLOR]

[SIZE="3"][[**PASTE** WINDOWS STANZA HERE!]][/SIZE]

[COLOR="Blue"]### BEGIN AUTOMAGIC KERNELS LIST
...[/COLOR]
```

5. **save** and **close** Gedit

P.S. As kernel updates happen, the "Automagic" list grows;
So, not only will your ``default 4'' _NOT_ boot Windows at that time,
it will actually boot Ubuntu with an _OLDer_ Linux kernel!!

---

### Post by jordanmthomas on 2008-02-05
The way asmoore suggested is probably not a bad idea, since Ubuntu adds entries to your grub as you accrue kernels.  I neglected to think of that since Arch lets me take care of grub stuff myself.

edit
asmoore has now edited his post to say the same thing, so this one is just downright useless now.

---

### Post by NStoker on 2008-02-05
Thanks guys!! I got it working,:guitar:

---

### Post by asmoore82 on 2008-02-05
If you want to stick with the "Windows is default but not at the top of the list" setup,
For it to work properly after a kernel update, you MUST uncomment(delete the leading ``#'') the line:
```
# updatedefaultentry=false
```
so that it looks like this:
```
updatedefaultentry=true
```

EDIT: and change ``false'' to ``true'' !!

---

### Post by Bothered on 2008-02-05
To change the default item in grub:

1. Press Alt+F2, and type: gksudo gedit /boot/grub/menu.lst
2. Somewhere near the top of the file a line reading "default 0" will appear. Change the number from 0 to the line in your grub menu corresponding to Windows. You can find this by scrolling to the bottom and counting how many lines starting with "title" there are *before* the line starting with "title" and containing the text "Windows".

e.g. for a typical dual boot setup there are 5 entries in the grub menu:

0 Ubuntu
1 Ubuntu (recovery)
2 memtest
3 A divider
4 Windows

Hence, in this case, you would change the line "default 0" to "default 4".

3. Save, exit, and reboot to see if the change has been successful.

---

### Post by Bothered on 2008-02-05
Oops, I was too slow.

> **asmoore82 said:**
> If you want to stick with the "Windows is default but not at the top of the list" setup,
For it to work properly after a kernel update, you MUST uncomment(delete the leading ``#'') the line:
```
# updatedefaultentry=false
```
so that it looks like this:
```
updatedefaultentry=false
```

Yes, you should also change this.

---

### Post by alzie on 2008-02-12
4. **paste** that stuff immediately before the "BEGIN AUTOMAGIC" line in blue...
```
[COLOR="Blue"]#
# Put static boot stanzas **before** and/or after AUTOMAGIC KERNEL LIST[/COLOR]

[SIZE="3"][[**PASTE** WINDOWS STANZA HERE!]][/SIZE]

[COLOR="Blue"]### BEGIN AUTOMAGIC KERNELS LIST
...[/COLOR]
```

Thanks for telling me where to put it before I went off on the update breaking my dual boot:lolflag:

---

