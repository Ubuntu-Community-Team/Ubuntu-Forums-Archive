---
title: "grub error 22: i have finally destroyed my computer"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by AvengingAngel718 on 2008-03-01
My tinkering has finally gotten the better of me.

so i've been messing with my hard drive a lot and repartitioning and stuff, and i set up an empty partition, installed windows, deleted it, and then repeated the process (install didnt work right, for some reason it doesnt recognize a lot of my hardware). For anyone who's ever dual booted with ubuntu installed first, you know this is a pain. I didnt really need windows, i was just playing around with it because i cant get Oblivion to install on Cedega. anyway i used my Ubuntu cd to repair GRUB, but now whenever i boot up it gives me GRUB error 22:No such partition found. 

I'm pretty sure this is because my ubuntu partition somehow got moved to /dev/sda2 when it used to be at /dev/sda1, and it's still trying to boot from the old location. I'm using the Live CD now, so is there a way to edit the boot path from the terminal? i'd rather not reinstall ubuntu.

Help me Ubuntu Forums. You're my only hope.

---

### Post by Duck2006 on 2008-03-01
gksudo gedit /boot/grub/menu.lst

you can edit your grub menu.lst file

You will have to look at your fstab to see it mounting the right partition to.

---

### Post by AvengingAngel718 on 2008-03-01
i used the command in the terminal and got this:

ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

(gedit:9611): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

then it opened a blank text file


also, my fstab file doesnt even refer to my main partition, which should be /dev/sda2:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by Duck2006 on 2008-03-01
Did you mount the drive first?

---

### Post by AvengingAngel718 on 2008-03-01
Can't, and this is why:

ubuntu@ubuntu:~$ mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab


so.....what now? haha

---

### Post by Duck2006 on 2008-03-01
sudo fdisk -l

and and post the output.

---

### Post by AvengingAngel718 on 2008-03-01
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19264   154738048+  83  Linux
/dev/sda3           19265       19457     1550272+   5  Extended
/dev/sda5           19265       19457     1550241   82  Linux swap / Solaris

---

### Post by ajmorris on 2008-03-01
hi there, 
put this in your /etc/fstab file:
```
/dev/sda2   /    auto    noatime    0 0
```
NOTE: auto can be replaced by your filesystem type e.g. ext3 if you wish
and the 0 0, can be changed, depending if you want filesystem checks at boot, etc.

Also, can you post your /boot/grub/menu.lst file please.

---

### Post by AvengingAngel718 on 2008-03-01
Trying to open my menu.lst file just opened a blank page after giving me this error:

(gedit:9611): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I'll try editing fstab and post in a few minutes to let you know if it worked.

---

### Post by ajmorris on 2008-03-01
> **AvengingAngel718 said:**
> Trying to open my menu.lst file just opened a blank page after giving me this error:

(gedit:9611): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Instead of using gedit, could you please try, sudo nano -w /boot/grub/menu.lst. Nano is a CLI text editor. Also, gksudo could be playing up, and resetting your Environment variables before opening gedit, so you could try do "su" first, then just running gedit /boot/grub/menu.lst without gksudo

---

### Post by AvengingAngel718 on 2008-03-01
> **ajmorris said:**
> Instead of using gedit, could you please try, sudo nano -w /boot/grub/menu.lst. Nano is a CLI text editor. Also, gksudo could be playing up, and resetting your Environment variables before opening gedit, so you could try do "su" first, then just running gedit /boot/grub/menu.lst without gksudo

Nano opened up a blank document as well 

	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)

Do i have to completely make a new document for it? it seems to have been wiped out

oh, and editing fstab didnt help, i still got error 22

---

### Post by ajmorris on 2008-03-01
> **AvengingAngel718 said:**
> Nano opened up a blank document as well 

    ](*,)    ](*,)    ](*,)    ](*,)    ](*,)    ](*,)    ](*,)    ](*,)

Do i have to completely make a new document for it? it seems to have been wiped out
can you paste the ouput of ```
ls -l /boot/grub
``` please

> oh, and editing fstab didnt help, i still got error 22
Editing fstab was to fix been able to mount /dev/sda2

---

### Post by AvengingAngel718 on 2008-03-01
> **ajmorris said:**
> can you paste the ouput of ```
ls -l /boot/grub
``` please


Editing fstab was to fix been able to mount /dev/sda2

ls: /boot/grub: No such file or directory

guys, what the hell did i do?

---

### Post by ajmorris on 2008-03-01
re-install grub
```
sudo apt-remove grub
``````
sudo apt-get install grub
```

---

### Post by AvengingAngel718 on 2008-03-01
Reinstalling grub didnt work. I even tried installing it off the CD and it didnt work, and the super grub live CD wont load it either. I'm thinking i have to do a reinstall *sigh*

it's possible to do that and move all my stuff over, right? maybe not programs, but docs at least?

---

### Post by ajmorris on 2008-03-01
yes, it is possible.
But i dont think you should need to re-install, did re-installing grub bring the /boot/grub folder back?

if not, do the following:
```
1 )sudo grub
```
```
2 )find /boot/grub/stage1
```
```
3 )root (hd#,#)
``` replace the #s by the numbers given by step 2
```
4 )setup (hd0)
```
```
5) quit
```

then you can reboot, but, if /boot/grub isnt there, then step 2 wont work, it will tell you it fails if it cant find the folder.

---

### Post by AvengingAngel718 on 2008-03-01
I did this before i posted the first time and again just a minute ago, because i've had this problem and fixed it that way before, but it didnt work either time. Grub is working fine, it just wont boot my partition. I have no idea how to fix this. Either it just doesnt recognize my partition or the partition's corrupted, I think.

---

