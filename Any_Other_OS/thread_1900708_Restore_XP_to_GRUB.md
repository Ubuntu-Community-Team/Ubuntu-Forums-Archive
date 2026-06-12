---
title: "Restore XP to GRUB"
date: 2011-12-27
forum: Any Other OS
---

### Post by upapilot on 2011-12-27
Hi,
I just installed Fedora 16 on my laptop.
However it seems GRUB has not installed properly and i cant seem to be able to boot into my old Windows XP.
Is there a way to restore windows XP to the GRUB menu?

[I know im not supposed to post fedora stuff here but i did want to go through the pain of registering on another forum. If you'd be so kind to help? :) ]

---

### Post by inobe on 2011-12-27
```
su -
(root password)

grub2-mkconfig -o /boot/grub2/grub.cfg
```

run that in fedora, it should scan and pickup xp, it should also add it to your grub menu.

haven't been using fedora for a wile, i won't be much help after this.

---

### Post by upapilot on 2011-12-27
This is the result of the command:
```

Found linux image: /boot/vmlinuz-3.1.0-7.fc16.i686
Found initrd image: /boot/initramfs-3.1.0-7.fc16.i686.img
  No volume groups found
Found Windows Vista (loader) on /dev/sda1
done

```

I used to have Vista long time ago but now i use XP *only*. What should i do next?

---

### Post by inobe on 2011-12-27
wow, man, looks like everything's messed up...

```
su -
(root password)

fdisk -l
```

btw does vista boot lols?

---

### Post by upapilot on 2011-12-27
this is the result of fdisk -l

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20482047    10240000   27  Hidden NTFS WinRE
/dev/sda2   *    20482048   253954047   116736000   83  Linux
/dev/sda3       254453535   377334719    61440592+   7  HPFS/NTFS/exFAT
/dev/sda4       377334720   488392064    55528672+   7  HPFS/NTFS/exFAT

```

No Vista doesnt boot up right. It keeps talking about some recovery cd.

BTW: 
If the blocks indicates the drive space, then Windows XP is on dev/sda4

---

### Post by inobe on 2011-12-27
maybe use gparted and rid of vista sda1, afterwords updating grub again. 

i maybe wrong, so you may want to get a second opinion, also get a live cd and backup your important data.

> BTW: 
If the blocks indicates the drive space, then Windows XP is on dev/sda4

sda3 is?

---

### Post by upapilot on 2011-12-27
> **inobe said:**
> afterwords updating grub again. 

And how do you do that?

sda3 is just storage (NTFS).

---

### Post by inobe on 2011-12-27
the command in post #2

it should recreate your /boot/grub2/grub.cfg and have xp included in it.

but again, i'm not certain removing vista will accomplish this.

may need to restore the mbr and start over.

---

### Post by raja.genupula on 2011-12-27
Hi man follow this link 
[http://ilovefedora.blogspot.com/2009/05/reinstall.html](http://ilovefedora.blogspot.com/2009/05/reinstall.html)

EDIT: [http://www.fedoraforum.org/forum/showthread.php?t=162898](http://www.fedoraforum.org/forum/showthread.php?t=162898)

---

### Post by upapilot on 2011-12-27
Hi raja,
You seem to have misunderstood my problem. The site you have given says what to do if your windows works fine and linux (grub) has disappeared.

My problem is the opposite. Linux (and grub) works fine but windows xp doesnt show up in the menu

---

### Post by inobe on 2011-12-27
removing vista and updating grub should send fedora back to sda1.

---

### Post by upapilot on 2011-12-27
Look i cant understand any of this.

Can you just tell me a process that adds Windows XP to Grub2?

---

### Post by upapilot on 2011-12-27
> **zong1 said:**
> 



Anyway, to add WinXP to GRUB2, without using the update-grub, then edit the file /boot/grub/grub.cfg and add these lines at the end of the file:
NB: Change the 9 value in hd0,9 to the disc you have Windows on.  If /dev/sda1 then change to hd0,1  (Mine is on on /dev/sda9).  
NB. there are two instances of hd0,9 to change.  
menuentry "Windows " {
set root=(hd0,9)
chainloader (hd0,9)+1
}
Afterwards, Windows will appear on grub at boot time.  If you run update-grub, the entry will disappear.  

If you want to make this a permanent change then edit this file:
/etc/grub.d/40_custom
and add the same lines as above to the end of the file. Shown below in bold below:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[B]menuentry "Windows " {
set root=(hd0,9)
chainloader (hd0,9)+1
}[/B]

Now run : update-grub


I tried to add windows using the second method (permanent one) but terminal says the update-grub command does not exsit.

---

### Post by inobe on 2011-12-27
i don't know how else to explain it.

using gparted from a live cd and deleting vista.

now from fedora

```
su -
(root password)

grub2-mkconfig -o /boot/grub2/grub.cfg
```


if that doesn't work, have a look here to restore the mbr.

[http://www.fedoraforum.org/forum/showpost.php?p=1535177&postcount=15](http://www.fedoraforum.org/forum/showpost.php?p=1535177&postcount=15)

i have no experience editing that file.

---

### Post by upapilot on 2011-12-27
Vista isnt on any partition i know of. sda4 is xp, sda3 is a drive for extra storage and sda2 is fedora (sda1 is free/unpartitioned).

---

### Post by inobe on 2011-12-27
```
Found linux image: /boot/vmlinuz-3.1.0-7.fc16.i686
Found initrd image: /boot/initramfs-3.1.0-7.fc16.i686.img
  No volume groups found
"Found Windows Vista (loader) on /dev/sda1"
done
```

grub found vista's loader on sda1.

my plan was to format sda1 with gparted, after that resize sda2 using sda1 formatted space thus increasing sda2 size.

after doing this, run in fedora

```
su -
(root password)

grub2-mkconfig -o /boot/grub2/grub.cfg
```

after that, the output should look similar to this this, a terrible example.

```
/dev/sda1 *    20482048   253954047   116736000   83  Linux
/dev/sda2 254453535   377334719    61440592+   7  HPFS/NTFS/exFAT
/dev/sda3 377334720   488392064    55528672+   7  HPFS/NTFS/exFAT

```

edit: of course, if that doesn't work, you can repair the mbr and reinstall grub on fedora with a live cd.

[http://www.fedoraforum.org/forum/showpost.php?p=1535177&postcount=15](http://www.fedoraforum.org/forum/showpost.php?p=1535177&postcount=15)

---

### Post by inobe on 2011-12-27
i have to get some sleep, goodnight, hope you get it sorted.

a bunch of info for you, you are not the only one this happened to.

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=fedora+16+add+xp+to+grub+menu#hl=en&sa=X&ei=d4r5TuGeAcPi0QG35cGxAg&ved=0CBcQBSgA&q=fedora+16+add+xp+to+grub+menu&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2f0b188327e19041&biw=1920&bih=937](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=fedora+16+add+xp+to+grub+menu#hl=en&sa=X&ei=d4r5TuGeAcPi0QG35cGxAg&ved=0CBcQBSgA&q=fedora+16+add+xp+to+grub+menu&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2f0b188327e19041&biw=1920&bih=937)

---

### Post by upapilot on 2011-12-27
> **inobe said:**
> i have to get some sleep, goodnight, hope you get it sorted.

a bunch of info for you, you are not the only one this happened to.

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=fedora+16+add+xp+to+grub+menu#hl=en&sa=X&ei=d4r5TuGeAcPi0QG35cGxAg&ved=0CBcQBSgA&q=fedora+16+add+xp+to+grub+menu&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2f0b188327e19041&biw=1920&bih=937](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=fedora+16+add+xp+to+grub+menu#hl=en&sa=X&ei=d4r5TuGeAcPi0QG35cGxAg&ved=0CBcQBSgA&q=fedora+16+add+xp+to+grub+menu&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2f0b188327e19041&biw=1920&bih=937)

Ok i did your commands and windows appeared on the boot menu
But when i try to boot in it says "NTLDR missing press Ctrl+alt+del to restart". OOps?

---

### Post by spiky001 on 2011-12-27
Hi  Have a read some google pages might help [HERE]("http://www.google.co.uk/#hl=en&sugexp=ppwc&cp=43&gs_id=78&xhr=t&q=NTLDR+missing+press+Ctrl%2Balt%2Bdel+to+restart&pf=p&sclient=psy-ab&source=hp&pbx=1&oq=NTLDR+missing+press+Ctrl%2Balt%2Bdel+to+restart&aq=0&aqi=g1g-v3&aql=f&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=440660d03c957758&biw=1024&bih=680")

---

### Post by upapilot on 2011-12-27
OOOPS sorry for the double post. refer to the next post pls :popcorn:

---

### Post by upapilot on 2011-12-27
Everything's become cluttered in this thread so ill give a recap:

Result of sudo fdisk -l is:

```


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac1df57b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        20482048   253954047   116736000   83  Linux
/dev/sda3       254453535   377334719    61440592+   7  HPFS/NTFS/exFAT
/dev/sda4   *   377334720   488392064    55528672+   7  HPFS/NTFS/exFAT


```


I went ahead and modified the /boot/grub2/grub.cfg file and added the following lines:
[code]
menuentry "Windows XP Professional" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos4)'
        search --no-floppy --fs-uuid --set=root 3464AFFC64AFBF4C
        chainloader +1
}

at this point when i go to windows xp it says invalid signature

---

### Post by oldfred on 2011-12-27
Moved to other OS sub forum.

Invalid signature usually means the NTFS partition does not have a valid NTFS boot sector - PBR. If that is your bootable NTFS partition use testdisk to recover from backup if valid or use Windows to run fixBoot & chkdsk to fix PBR.

Post this to see what is where, not sure exact commands in Fedora to make sure gawk & xz-utils are installed or not.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

