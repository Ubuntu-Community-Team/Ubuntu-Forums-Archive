---
title: "cant boot"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by spadhawk on 2008-03-12
ok  when i try to boot it gets past the bios and past grub and then sitts on a black screen ad does nothiing so i tryed to boot in recovery mode and it said```

 [    11.791358] pkease append a correct "root=" boot option; here are the available partitions:

[    11.971444] Kerel panic - not syncing: VFS: unable to mount root fs on unknowen-block(0,0)
```

---

### Post by dstew on 2008-03-12
Are you trying to boot an installed Ubuntu system? Was it working before? Did you do anything that might have made it stop working?

---

### Post by spadhawk on 2008-03-12
its already installed and i was working for mounths but i installed a Usplash and now that happens

---

### Post by spadhawk on 2008-03-12
please guys i realy need to have my comp back 
like i had it set upp so nice it was such an awsome setup

---

### Post by sandysandy on 2008-03-12
please boot from live Cd and post [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by spadhawk on 2008-03-12
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc329e402

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       151589340   156296384     2353522+  82  Linux swap / Solaris
/dev/sda2        39680550   151589339    55954395   83  Linux
/dev/sda3   *          63    39680549    19840243+  83  Linux

Partition table entries are not in disk order
``` thanks in advance for the help

---

### Post by bodhi.zazen on 2008-03-12
Looks like your partitions are off, (hd0,0) looks to be your swap partition.

Try re-installing grub. You need to determine which is your root partition

sda2 = (hd0,1)
sda3 = (hd0,2)

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by spadhawk on 2008-03-12
i that didn work 

but  mey not have done it perfectly could i get some help

---

### Post by bodhi.zazen on 2008-03-12
What did you do ?

Do you know which partition is your ubuntu root partition ?

Error message ?

---

### Post by spadhawk on 2008-03-12
umm i said the error message and i don't know the partition  and i was just trying to install a uslpash and it worked at first but was really small so i changed the resolution to 600x800 i think  of the usplash then it showed it when i was shutting down

---

### Post by spadhawk on 2008-03-12
ohh and guys the program that i used to change the resolution is "start up manager"

---

### Post by unutbu on 2008-03-12
Have you tried changing /etc/usplash.conf back to the old resolution?

---

### Post by TheDilettante on 2008-03-12
Hawk, boot in safe/recovery mode.  Log in and type:

cat /boot/grub/menu.lst

and print the output here.  This will show from which drive Ubuntu is attempting to boot, as well as any possible grub errors.  I know you tried to reinstall it... Let's see how it went.

---

### Post by Kedster on 2008-03-13
LOL IM ACTUALLY SPADHAWK lol i wasn't able to use my comp so i used my dads and he was loged in so i accidentally  used his account 

hey guys sorry for not replying i decided to do a total reinstall (homes on a separate partition so its easy) but TheDilettante i wasn't able to boot to recover mode. i would have  done it

---

