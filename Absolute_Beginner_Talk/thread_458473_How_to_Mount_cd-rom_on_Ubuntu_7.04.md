---
title: "How to Mount cd-rom? on Ubuntu 7.04"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by David4 on 2007-05-29
Hi, having a hard time with some prgms.
Have installed SoundJuicer and works just fine,reads and plays my CD
When try to use other Pgms such as Serpentine,Totem Movie Player returns a error message "Could not mount CD-Rom1 or 2"
On file, under Media I can see both cd-roms but "empty"
But on Desktop I can only see my USB external HD as well as SD disk I have
Seems I need to mount these devices?
any ideas?
thank you David

---

### Post by Happy_Man on 2007-05-29
In a terminal: (System --> Accessories --> Terminal)

```
sudo mkdir /media/CD
sudo mount /dev/scd0 /media/CD
```

---

### Post by init1 on 2007-05-29
> ```

sudo mkdir /media/CD
sudo mount /dev/scd0 /media/CD

```
Actually, the location of the CD drive will vary. On my computer I would do,
```

sudo mkdir /media/CD
sudo mount /dev/hda /media/CD

```
You would need to find the device. 
In the main menu there is a hardware finder. Maybe it is in there

---

### Post by David4 on 2007-05-29
Well tried all combinations I can think of and these are the results
david@david-desktop:~$ sudo mkdir /media/CD
mkdir: cannot create directory `/media/CD': File exists
david@david-desktop:~$ sudo mount /dev/scd0 /media/CD
mount: special device /dev/scd0 does not exist
david@david-desktop:~$ sudo mount /dev/scd0 /media/CD
mount: special device /dev/scd0 does not exist
david@david-desktop:~$ sudo mount /dev/hda /media/CD
mount: special device /dev/hda does not exist
david@david-desktop:~$ sudo mount /dev/scd0 /media/CD
mount: special device /dev/scd0 does not exist
david@david-desktop:~$ sudo mount /dev/scd0 /media/CDcdrom0
mount: mount point /media/CDcdrom0 does not exist
david@david-desktop:~$

---

### Post by init1 on 2007-05-29
Ok, you are doing what you need to do, but you need to find the cd drive dev. On mepis, my cd rom was linked to /dev/cdrom, so
```
sudo mount /dev/cdrom /media/CD
```
might work

---

### Post by David4 on 2007-05-30
Well here is my last attempt

david@david-desktop:~$ sudo mount /dev/cdrom0/media/cd
Password:
mount: can't find /dev/cdrom0/media/cd in /etc/fstab or /etc/mtab
david@david-desktop:~$ 

this is absurd but just cannot do it right.
on files i have the following

File System
Media 
cdrom0
cdrom1


I know am typing the wrong command but what else?
thanks
David

---

### Post by init1 on 2007-05-31
> **David4 said:**
> Well here is my last attempt

david@david-desktop:~$ sudo mount /dev/cdrom0/media/cd
Password:
mount: can't find /dev/cdrom0/media/cd in /etc/fstab or /etc/mtab
david@david-desktop:~$ 

this is absurd but just cannot do it right.
on files i have the following

File System
Media 
cdrom0
cdrom1


I know am typing the wrong command but what else?
thanks
David
This is how mounting works
sudo mount /dev/*** /folder
sudo allows you to run special commands like mount
mount actually mounts it
/dev/*** is the device
/folder is the mount point. If it works, the contents of the cd will appear in the folder
Try these. If one works, you don't need to try the others. 
```

mkdir /media/CD
sudo mount /dev/cdrom0 /media/CD
ls /media/CD
sudo mount /dev/cdrom1 /media/CD
ls /media/CD
sudo mount /dev/cdrom /media/CD
ls /media/CD

```
If all goes well, the files on the CD should be displayed by now

---

### Post by Happy_Man on 2007-05-31
> **David4 said:**
> Well here is my last attempt

david@david-desktop:~$ sudo mount /dev/cdrom0/media/cd
Password:
mount: can't find /dev/cdrom0/media/cd in /etc/fstab or /etc/mtab
david@david-desktop:~$ 

this is absurd but just cannot do it right.
on files i have the following

File System
Media 
cdrom0
cdrom1


I know am typing the wrong command but what else?
thanks
David

There has to be a space between "/dev/cdrom0" and "/media/cd".

---

### Post by 213374U on 2007-05-31
I love these forums!!! Just reading through solved the problem I've been messing with for the past hour.

Thanks

```
kyle@kyle-desktop:~$ mkdir /media/CD
mkdir: cannot create directory `/media/CD': File exists
kyle@kyle-desktop:~$ sudo mount /dev/cdrom0 /media/CD
mount: special device /dev/cdrom0 does not exist
kyle@kyle-desktop:~$ ls /media/CD
kyle@kyle-desktop:~$ sudo mount /dev/cdrom1 /media/cd
mount: mount point /media/cd does not exist
kyle@kyle-desktop:~$ sudo mount /dev/cdrom /media/CD
mount: No medium found
kyle@kyle-desktop:~$ sudo mount /dev/cdrom /media/CD
mount: block device /dev/cdrom is write-protected, mounting read-only
kyle@kyle-desktop:~$ ls /media/CD
100_0534.JPG  100_0559.JPG  100_0573.JPG  100_0589.JPG  100_0606.JPG
100_0535.JPG  100_0560.JPG  100_0574.JPG  100_0590.JPG  100_0610.JPG
100_0537.JPG  100_0561.JPG  100_0575.JPG  100_0591.JPG  100_0611.JPG
100_0538.JPG  100_0562.JPG  100_0577.JPG  100_0592.JPG  100_0612.JPG
100_0547.JPG  100_0564.JPG  100_0578.JPG  100_0593.JPG  100_0617.JPG
100_0548.JPG  100_0565.JPG  100_0579.JPG  100_0597.JPG  100_0618.JPG
100_0550.JPG  100_0566.JPG  100_0581.JPG  100_0598.JPG  100_0620.JPG
100_0551.JPG  100_0568.JPG  100_0582.JPG  100_0599.JPG  100_0621.JPG
100_0552.JPG  100_0570.JPG  100_0584.JPG  100_0600.JPG  100_0622.JPG
100_0556.JPG  100_0571.JPG  100_0585.JPG  100_0602.JPG  100_0624.JPG
100_0558.JPG  100_0572.JPG  100_0587.JPG  100_0603.JPG  100_0626.JPG

```

---

### Post by struess on 2007-06-01
```
sudo mkdir /media/CD
sudo mount /dev/cdrom /media/CD
```

like a charm :)

edit:  to use programs that normally recognize your mount point as /media/cdrom0 (e.g. DVD-playing programs on Dapper, for me), just change     /media/CD    --->   /media/cdrom0

---

