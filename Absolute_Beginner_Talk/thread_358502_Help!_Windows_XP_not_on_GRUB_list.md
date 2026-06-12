---
title: "Help! Windows XP not on GRUB list"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-02-10
I have just installed Ubuntu 6.10 on my computer that also is running Windows XP Pro.  I made sure to not delete my XP partition during installation, and the XP folder shows up on my Ubuntu desktop. BUT, I cannot boot to XP, it is not in the GRUB list.

What do i do?  I can reinstall XP, but I would rather not.

Thanks!

---

### Post by towsonu2003 on 2007-02-11
you don't have to reinstall it. in fact if you do, it will overwrite grub... 

can you please provide the output of 
```
sudo fdisk -l
``` in a terminal (Applications>Accessories>Terminal) and explain in which partition you have the XP?

---

### Post by mdknaebel on 2007-02-11
This is what it says:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1530    12289693+  83  Linux
/dev/hda2            1531        9732    65882565    f  W95 Ext'd (LBA)
/dev/hda5            1531        9732    65882533+   7  HPFS/NTFS

---

### Post by towsonu2003 on 2007-02-11
> **mdknaebel said:**
> This is what it says:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1530    12289693+  83  Linux
/dev/hda2            1531        9732    65882565    f  W95 Ext'd (LBA)
/dev/hda5            1531        9732    65882533+   7  HPFS/NTFS

thanks. Add the following to the end of your /boot/grub/menu.lst -be **very** careful while doing this, no typos etc :)

To do that, in a terminal, type:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst
``` when you see the file opened up, at the end of that file, add:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Home Edition
root            (hd0,4)
savedefault
makeactive
chainloader     +1

```

Reboot and the entry should now be there and working...

To give an example of how this works, I'll provide you with my partitions and my grub.lst:

sudo fdisk -l:
```

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/**hda1**   *           1        1824    14651248+   7  **HPFS/NTFS**
/dev/hda2            1825       12161    83031952+   5  Extended
/dev/hda5            1825        2067     1951866    b  W95 FAT32
/dev/**hda6**            2068        3283     9767488+  83  **Linux**
/dev/hda7            3284        3405      979933+  82  Linux swap / Solaris
/dev/**hda8**            3406       10700    58597056   83  **Linux**
/dev/**hda9**           10701       11465     6144831   83  **Linux**
/dev/**hda10**          11466       12161     5590588+  83  **Linux**

```
So I have Windows at hda1, Ubuntu at hda6, 2 other distros at hda 9, 10, home at hda8
Here is the grub.lst that shows it:
```

...

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-27-686
root            (**hd0,5**)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (**hd0,5**)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda6 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (**hd0,0**)
savedefault
makeactive
chainloader     +1

title           Zenwalk
root            (**hd0,8**)
savedefault
chainloader     +1

title           Slackware
root            (**hd0,9**)
savedefault
chainloader     +1

```

---

### Post by mdknaebel on 2007-02-11
Hmm... I am kind of lost... (Sorry)

When and where do I put the first code you gave?  Do I type it exactly the way you have it? Or, do I have to put in my own values?

Thanks

---

### Post by mdknaebel on 2007-02-11
Actually, I did figure out the first part. I copied and pasted (is that OK?) and the file opened up.  then, using the second code you supplied and your example, I copied and pasted the second code into the file at then end.

But, when I rebooted, Windows XP Home Edition (I have Professional) showed up on the boot menu but I got an error saying it was invalid when I selected it.

What should I do?

Thanks

---

### Post by towsonu2003 on 2007-02-11
> **mdknaebel said:**
> Hmm... I am kind of lost... (Sorry)

When and where do I put the first code you gave?  Do I type it exactly the way you have it? Or, do I have to put in my own values?

Thanks
That's okay :) I confuse myself at times as well...

hmm, I'll explain but if it still is confusing, you can copy paste the output of ```
cat /boot/grub/grub.lst
``` and I'll show how to change the file. 

basically, you input this command:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
which makes a backup of the configuration file of grub (just in case). Then you do
```
sudo gedit /boot/grub/menu.lst
``` to open the configuration file, scroll to the end, and add the following
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Home Edition
root            (**hd0,4**)
savedefault
makeactive
chainloader     +1
```

I already adjusted the value (in bold) according to your partition info.

---

### Post by mdknaebel on 2007-02-11
Hmm... Ok, I did that but still an error at boot.  My XP Professional is on hda5, according to my partion table, should it be instead:

title        Microsoft Windows XP **Professional**
root         (**hd0,5**)

I dont know if this is right, but it seems logical.

Thanks

---

### Post by towsonu2003 on 2007-02-11
> **mdknaebel said:**
> 
But, when I rebooted, Windows XP Home Edition (I have Professional) showed up on the boot menu but I got an error saying it was invalid when I selected it.


No need to worry about the name it shows. You can edit it to your needs :)

this part of your partition is confusing to me:
```
/dev/hda2 1531 9732 65882565 f W95 Ext'd (LBA)
```

Try replacing this part in that file:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP **Home Edition**
root            (**hd0,4**)
savedefault
makeactive
chainloader     +1
```
**with** this new version:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP **Professional**
root            (**hd0,1**)
savedefault
makeactive
chainloader     +1
```

As I mentioned, the name (Home, Professional) doesn't matter. we're now trying to see if it will boot using hda2 instead of hda5... I got this idea from: [http://www.linuxquestions.org/questions/showthread.php?t=324598](http://www.linuxquestions.org/questions/showthread.php?t=324598)

**Edit**: grub's weird :) in grub's language, hda2 = hd0,1 hda5 = hd0,4 hdb10 = hd1,9 hde25 = hd4,24 (you start counting from zero, or substract 1 from the fdisk hd values. I'm pretty sure I couldn't explain myself nicely but... eheh :)

---

### Post by mdknaebel on 2007-02-11
Hmmm.... I still get an error after selecting Windows XP when booting:

Error 12: Invalid device requested

Any Ideas?

Thanks!

---

### Post by towsonu2003 on 2007-02-11
> **mdknaebel said:**
> Hmmm.... I still get an error after selecting Windows XP when booting:

Error 12: Invalid device requested

Any Ideas?

Thanks!

weird... we tried both hd0,1 (hda2) and hd0,4 (hda5)... and it doesn't like them. you made sure that there is **no** space in the string hd0,1 or hd0,4 right?

I'm out of ideas... And this post has too many replies for others to check out. If I were you, I would open a new thread to ask for help with the following info:

title: can't boot XP, "invalid device requested"

in the text, include:
1. output of sudo fdisk -l
2. output of cat /boot/grub/menu.lst
3. that you tried putting hd0,1 and hd0,4 but you got the same errors...
4. a link to this thread

hopefully someone might be able to help that way. can you also provide a link to your new thread here, I'd like to monitor and learn why this is happening...

As a last resort, you can try to recover XP's bootloader and try reinstalling Ubuntu's bootloader over it. To recover XP's bootloader, do:
Boot from the Windows XP install disc, select Recovery Console from boot menu and run ```
fixmbr
```. It will overwrite grub. Reboot and Windows will open up.

To recover grub, see: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) but I doubt it will catch Windows when reinstalled... sorry couldn't help

---

### Post by mdknaebel on 2007-02-11
Thank you so much for your time and effort anyway, hopefully this will get it figured out!

[http://ubuntuforums.org/showthread.php?p=2140360#post2140360](http://ubuntuforums.org/showthread.php?p=2140360#post2140360)

---

### Post by confused57 on 2007-02-11
I'm not an expert, but I see 2 possible problems with the setup...Windows on a logical partition and being located on a partition after Ubuntu's partition.

towsonu2003's last resort suggestion may work...


On a single hard drive, it's easier to set up a dualboot with Windows & Ubuntu if Windows is located on a partition before Ubuntu's & Windows preferably on a primary partition...Ubuntu doesn't mind being on a logical partition.

---

