---
title: "triple boot query"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-04-17
I have Sabayon Linux and XP workling well on a new PC. I wish to install Edgy/Fiesty on another partition to run as a triple boot. I have looked at Hermans Zone for assistace and find two options; Chainloader, and Configfile.
 
Configfile requires; 
 
title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,5)/boot/grub/menu.lst
 
Chainloader requires:
 
title        Ubuntu Edgy Eft
root        (hd0,5)
savedefault
chainloader    +1
 
But chainloader also requires: Edgy Eft is a Linux operating system on partition number 6, and it has Grub installed in the first sector of the partition.

Question. Which option is the best for me to  use as I will use the Sabayopn Grub to load XP and Edgy? If I use the second option how do I ensure that GRUB is loaded into the first part of the Edgy partition?
 
Tony

---

### Post by freebird54 on 2007-04-17
Configfile is a wonderful thing if you are running multiple drives, as well as multiple OS's.  That way,  you can operate in paranoia mode if you wish, and have ONLY the drive you are installing to visible during the install - eliminates the less enjoyabole possibilities..  Then - hook up the main drive(s), add a configfile entry, and away you go!

The other advantage is that any changes to the 'added' system, such as upgraded kernels, are handled 'locally', and your 'main' system stil just points to the auto-updated menu.lst on your target.

(quad boot right now - but 3 are Ubuntu.  Edgy working, Edgy test, Feisty test - oh and XP)

---

### Post by dstew on 2007-04-17
I agree that using configfile is best. However, you can easily put grub into the boot sector of your Ubuntu partition, using the grub command line. Start grub from your other linux distribution, and on the grub command line:

grub>root (hd0,5)
grub>setup (hd0,5)
grub>quit

That should put grub stage 1 and 1.5 into the boot sector of partition 6. You might get another grub menu when you boot that partition, but you can fix that later.

---

### Post by Terl on 2007-04-17
I have windows xp and 3 linux distros loaded up.  Windows was already there.  I installed Ubuntu first and let its grub go to mbr.  For the other distros I tell their loader to go to their / partition.  Then I just boot into Ubuntu fix up my menu.lst with the new distro's info and save it.  Easy as pie.

---

### Post by tchoklat on 2007-04-23
Yeh, that is in effect what I did. XP on first, Sabayon second with grub to MBR ( I think anyway, as where else would it go) then two other distros with their loader to / though even after amending the Sabayon menu.lst they do not load. Something simple is worng and I cannot work it out!
 
What would happen hough if no, loader is put to the MBR? Will anything load? Sabayon loads first to its menu.lst - does this mean it has it's loader on the MBR?

---

### Post by freebird54 on 2007-04-23
Are you chainloader'ing them?  Or, configfile is better.  Here's a sample from mine...

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title           Microsoft Windows XP Professional

root    (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu Feisty Test System
savedefault
configfile      (hd1,5)/boot/grub/menu.lst
```


That's the easiest - as changes to each distros menu.lst are up to them, without affecting your primary menu.lst (and less editing!)

---

