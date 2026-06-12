---
title: "Dual booting with WinXP"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by Souljah on 2005-10-11
Well now that I know how to install ubuntu, I didn't probably set it up so that I can share files with windows. I mean, I'm sharing my internet connection but I don't believe it's the same. Anyway, what are the options or setup procedures for dual booting with windows xp professional edition. It's all ready installed on this notebook by the way, but for some reason it's not a boot up option and by default it goes straight to ubuntu. I don't know what I did, I must have changed some kernel by messing around I guess. If there's a way to retrieve it, please let me know guys. I guess both partitions would have to be FAT32, not ntfs huh. 

Ryan

---

### Post by SilentCacophony on 2005-10-11
Hi. It's a bit unclear to me what the problem is. It should help if you copy and paste the results of these two commands here, I think:

Open the gnome terminal (Applications > Accesories > Terminal) and:

**sudo fdisk -l**

**cat /boot/grub/menu.lst**

---

### Post by mit on 2005-10-11
No, you can have the windows partition formated in NTFS. 
If you already have a partition within Windows you are laughing. :) 

Say, Windows is installed in C: and you have made a logical drive of D: All you have to do is move whatever files you have onto C: and there is your partition :KS 

Set your BIOS to boot from the CD. Ubuntu will then go through set-up and inform you there is another Operating System installed and would you like to point it where to install.

If you select D: it will warn you that you will loose data, but then you don't need it because you have moved or backed it up anyhow. 
It will then install Grub and when you turn your PC on you will have a menu asking which OS to boot from.

There are many ways you can dual boot and i'm sure they will follow. :)

---

### Post by raspa_sete on 2005-10-11
the program you use for booting is probabily GRUB.


about the default choice on the boot:
go to linux and open a shell,

(I use "pico" as a text editor)

so if you do:  ```
 pico /boot/grub/menu.lst
```

you will open the settings file for the grub-boot. If you take a look at this file, along with the option of how lon the computer will wait for your answer you will get:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0
```

this last option, the "default 0" mens that the default option to boot is the first after the line

```
## ## End Default Options ##
```

which in my case is the linux, if you want to change this, just see in which position windows comes. NOTE THAT THE COUNT STARTS IN ZERO, if you have 4 boot option and windows is the last, you should modify the "default 0" code to "default 3". clear?

Now, if you don't have the windows option then (then something is wrong and) you have to add it to the GRUB line. for that, just edit the file above "/boot/grub/menu.lst" and add the following to the end, (before you do this end reading)

```
title           Microsoft Windows XP Professional
root            (hd0,0)
makeactive
chainloader     +1

``` 

do you see the "(hd0,0)", the first part "hd0" means in which hard disk the windows is in, and the other zero is in which partition in that disk. the above works for me, I had windows installed in the first partition of the disk then installed linux (thats why that line for ubuntu is probabily a (hd0,3) or (hd0,2)). normally the windows would appear in the grub option i don't know if you installed ubuntu on top of the windows partition...

About seeing your windows partition with linux, that's another talk.
You have to mount the windows partition by editing the "/etc/fstab" and here I can't help you (sorry) but take a look at the ubuntu starter guide, they give some lines in how you can do that: [http://ubuntuguide.org/](http://ubuntuguide.org/)

cheers

---

### Post by Souljah on 2005-10-11
[QUOTE=SilentCacophony]Hi. It's a bit unclear to me what the problem is. It should help if you copy and paste the results of these two commands here, I think:

Open the gnome terminal (Applications > Accesories > Terminal) and:

**sudo fdisk -l**

**cat /boot/grub/menu.lst**[/QUOTE]

Here's the result for the sudo fdisk command:

[B]Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        3648     8819685    5  Extended
/dev/hda5            2551        3648     8819653+  8e  Linux LVM
[/B]

Here's the result for the cat /boot/grub/menu.lst:

**cat: /boot/grub/menu.lst: No such file or directory**

Also, if I do the command * pico /boot/grub/menu.lst*, I get the pico editor but it's all blank. Nothing comes up.

EDIT: The actualy problem is that when my computer starts up, it goes straight to the ubuntu load up process. I can't even access my BIOS by repeatedly presssing F2. I can however press F12 which allows me to boot from CD.

---

### Post by SilentCacophony on 2005-10-11
> Here's the result for the cat /boot/grub/menu.lst:

cat: /boot/grub/menu.lst: No such file or directory

Also, if I do the command pico /boot/grub/menu.lst, I get the pico editor but it's all blank. Nothing comes up.

Hmm. That's decidedly odd. I'm not too sure how Linux LVM works, but looks to me as if Ubuntu is on hda5, and Windows is still on hda1. Why you don't have grub's boot menu, I don't know. Try this in the terminal:

**sudo update-grub**

and enter** y** when asked if you want to generate a list. If it works, then:

**sudo gedit /boot/grub/menu.lst**

and after this line (should be at bottom):

*### END DEBIAN AUTOMAGIC KERNELS LIST*

add this entry:

[I]title		Windows XP
root		(hd0,0)
makeactive
savedefault
chainloader	+1[/I]

then save it. That should do it.

---

### Post by SilentCacophony on 2005-10-11
You may want to copy and paste back the /boot/grub/menu.lst file after you're done editing it, if that works, just to make sure it looks right.

---

