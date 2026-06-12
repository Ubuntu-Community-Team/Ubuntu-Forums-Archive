---
title: "Ubuntu \ Fedora and David Copperfield..."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-09-16
Hi all.

I installed Fedora today on my other drive and it made Ubuntu disappear. :( 

Setup...

Hdd 0 >Winxp pro >WD 80gig

Hdd 1 >Fedora 7 >Maxtor 80gig

Hdd 2 >Ubuntu Feisty > WD 180gig 

All IDE's. 

I had WinXP installed, had Ubuntu installed prior to Fedora. I installed Fedora and now Ubuntu has left the building. :confused:

After some reading, most suggest going into Ubuntu and Fedora and modify the grub loader, however, this may be impossible if  I can't access Ubuntu at all, only Windows or Fedora. I know it's there, I just can't get to it. 


Any suggestions...? Thanks,

Paul

---

### Post by por100pre1 on 2007-09-16
Login into Fedora.Try to locate menu.lst:

```
locate menu.lst
```

post the results...

Check if you can use fdisk in Fedora (you could need to be root for this):

```
fdisk -l
```

post the results...

---

### Post by benerivo on 2007-09-16
Can you access the Ubuntu drive from from Fedora?

What you need to do is alter /boot/grub/menu.lst in the Fedora installation so that it includes a pointer to Ubuntu. If you can find out what the entry is in your Ubuntu's /boot/grub/menu.lst then you can just copy that to Fedora's. Mine is...

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,3)
kernel	/boot/vmlinuz-2.6.20-16-generic root=UUID=8c7d89iff-9d8c-47fjh8 ro quiet splash
initrd	/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

The only difference yours would have to mine would be that your root would have to reflect what drive Ubuntu is on on your machine (ie. (hd0,3), and your UUID would be different. To find out what these are, go in to a Fedora terminal and check the results of...```
blikd
```. This should give you the UUID and you will probably guess what the drive is. When you enter the drive numbers next to 'root' you have to start both numbers from '0'. Example...

hda1 is (hd0,0)
hdb3 is (hd1,2)

Your Ubuntu is on Hdd 2 so is probably going to be...

hdc1 which is (hd2,0)

---

### Post by gimpguy2000 on 2007-09-16
> **por100pre1 said:**
> Login into Fedora.Try to locate menu.lst:

```
locate menu.lst
```

post the results...

Check if you can use fdisk in Fedora (you could need to be root for this):

```
fdisk -l
```

post the results...


Thanks. Unfortunately I have nothing to report as it only says no such file or directory for your first code, and the fdisk -l says command not found and I am in root. 

TX

Paul

---

### Post by splintercellguy on 2007-09-16
My menu.lst is in /boot/grub, is it in there?

---

### Post by DezSP on 2007-09-16
What exactly do you mean by disappeared? Have you tried booting directly from the Ubuntu HDD, rather than the Windows/Fedora one?

---

### Post by gimpguy2000 on 2007-09-16
> **benerivo said:**
> Can you access the Ubuntu drive from from Fedora?

What you need to do is alter /boot/grub/menu.lst in the Fedora installation so that it includes a pointer to Ubuntu. If you can find out what the entry is in your Ubuntu's /boot/grub/menu.lst then you can just copy that to Fedora's. Mine is...

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,3)
kernel	/boot/vmlinuz-2.6.20-16-generic root=UUID=8c7d89iff-9d8c-47fjh8 ro quiet splash
initrd	/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

The only difference yours would have to mine would be that your root would have to reflect what drive Ubuntu is on on your machine (ie. (hd0,3), and your UUID would be different. To find out what these are, go in to a Fedora terminal and check the results of...```
blikd
```. This should give you the UUID and you will probably guess what the drive is. When you enter the drive numbers next to 'root' you have to start both numbers from '0'. Example...

hda1 is (hd0,0)
hdb3 is (hd1,2)

Your Ubuntu is on Hdd 2 so is probably going to be...

hdc1 which is (hd2,0)


Thanks for the reply, when I enter the command , this is what I get...
> 
[root@localhost gimpguy]#  /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
[root@localhost gimpguy]# 

Even in root I have no rights...lol...

TX
Paul

---

### Post by gimpguy2000 on 2007-09-16
Here...I  did a    cat menu.lst and it worked...:)

splashimage=(hd1,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.21-1.3194.fc7)
        root (hd1,0)
        kernel /vmlinuz-2.6.21-1.3194.fc7 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.21-1.3194.fc7.img
title Ubuntu
        rootnoverify (hd2,0)
        chainloader +1
title Other
        rootnoverify (hd0,0)
        chainloader +1


Now to figure out what's going on...


EDIT: I can't get the uuid, blikd , when I type it, it says command not found. Else I copied the rest into the config.

---

### Post by gimpguy2000 on 2007-09-16
Update :

I used this     ** ls /dev/disk/by-uuid**  and I got 3 sets of UUIDs, but they are not in order or anything and it won't list the device that way.... Would it hurt to try each one or not recommended?

---

### Post by gimpguy2000 on 2007-09-17
SOLVED

I can't have Fedora and Ubuntu so I took Fedora off. No matter what I did, how I installed, they will not coincide with each other. I even had help over in the Fedora forum and that didn't work either. They mentioned a bug  so we'll see and if so, that would explain a lot. 

Thanks

Paul

---

### Post by rusloc on 2008-01-05
> **gimpguy2000 said:**
> I can't have Fedora and Ubuntu so I took Fedora off. No matter what I did, how I installed, they will not coincide with each other.My situation is nearly identical, only I have three SATA hdd's. My Fedora and Ubuntu installations also were 'leaving the building' after the other was installed. They were actually there but the grub editing didn't do much, and only the last linux installed was booting.

I saw all sort of errors: 'Unknown file system, drive" and so on. But I kept experimenting and installing/reinstalling.

Even though my last hdd-based grub window showed all three OS's, only Ubuntu 7.10 and Windows XP were bootable, but miraculously after selecting some line in the Super Grab Disk I finally managed to boot into  Fedora Core 8 as well.

Apparently Fedora and Ubuntu may **co-exist** on the same machine!

---

