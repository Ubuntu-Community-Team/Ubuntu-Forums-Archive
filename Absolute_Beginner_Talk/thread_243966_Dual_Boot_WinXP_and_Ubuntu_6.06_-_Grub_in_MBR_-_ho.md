---
title: "Dual Boot: WinXP and Ubuntu 6.06 - Grub in MBR - how can I make WinXP boot by default"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by patslap on 2006-08-25
Hi 

How can I make WinXP boot by default - I have put Grub in Windows MBR, and Ubuntu boots after the timeout. I want WinXP to boot after timeout by default.

I've checked many formums and wikis bu they mostly seem to be saying that I should have installed Grub on the same hard disk as Ubuntu is installed on! Too late for me now!

WinXP is installed on HD0, Ubuntu is installed on HD1.

This is the /boot/grub text:

[INDENT]## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/INDENT]

What do I need to edit to make Win XP default boot option. 

Many thanks for your help.

---

### Post by mssever on 2006-08-25
Look at the GRUB menu and count the entries starting from 0 until you get to the WinXP item. Then, edit /boot/grub/menu.list and put the line
```
default x
``` where x is the number that you previously determined. The file probably says default 0 right now. Next, run ```
sudo update-grub
```

That should do it.

---

### Post by benfindlay on 2006-08-25
Your grub.lst file will have a bit that reads as follows:

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

Changing the 0 at the "Default 0" to 3 in your case should do the trick, but MAKE A BACKUP FIRST! ;)

---

### Post by Bachstelze on 2006-08-25
Hi and welcome on board :)

A little search on the Wiki would have brought you to

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by confused57 on 2006-08-25
I think the default should be 4...

title Other operating systems:
root


also counts as an OS entry...someone else previously pointed this out to me.

---

### Post by patslap on 2006-08-25
:) Thanks for your speedy replies - sorted this now. 


Many thanks

patslap.

---

### Post by benfindlay on 2006-08-25
Not quite sure what you're refering to with "root"

I don't think it does affect it. Each kernel you have installed is listed separately, along with a recovery mode for each kernel, and you also have a memtest listed.

Then winxp is usually listed straight after that. At least last time I dual booted I ignored any reference to root in the file and it worked fine.

But as long as all you're changing is the "default 0" line, then it won't matter if you get it wrong, just manually choose to boot standard ubuntu and edit it again!

Learn by doing, thats how I make all my best mistakes! ;)

---

