---
title: "noob add hardware ?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2007-08-16
Hi all,

This will be my first post, and I should warn you that I am a complete newbie to anything linux.

I started with Apple when I was younger, and have since switched to windows (For the last 10 years or so). Today was my first experience with any linux OS at all, and I am pretty proud to have installed and configured (basics) kubuntu 7.04 feisty fawn on my own.

I do not fully understand how linux works, nor am i fully comfortable navigating the system....i've spent the last couple hours pouring over some online wiki's and user guides but am still having  a couple basic problems...

that said, i have 2 questions for some kind soul out there...

1)  I have an intel pro wireless 3945abg network card.... how do i install this hardware/configure in kubuntu?

2) I have a 250gig external usb hd that I cannot seem to access through kubuntu. do i need to install drivers ?

many thanks,

---

### Post by Hobo Joe on 2007-08-16
1. I'm not familiar with Kubuntu so I can't really help you here. 

2. It's probably not mounted, try running the command: 
```

sudo fdisk -l

```
(that's a lowercase 'L')
Make sure your drive is plugged in when you run that command.

---

### Post by sysikon on 2007-08-16
1. [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless")

2. Do you have usbutils installed? Check Synaptic. System>Administration>Synaptic

---

### Post by sonofusion82 on 2007-08-16
> **Hobo Joe said:**
> 1. I'm not familiar with Kubuntu so I can't really help you here. 

2. It's probably not mounted, try running the command: 
```

sudo fdisk -l

```
(that's a lowercase 'L')
Make sure your drive is plugged in when you run that command.

yes, kubuntu has this problem with not mounting external USB NTFS partitions, FAT32 are fine.

after you figure out the the device with fdisk command above, you can mount /dev/sd??  with the mount command like
sudo mount -t auto -o umask=000 /dev/sd??  mount_point

---

### Post by tango_ninja on 2007-08-16
i don't have my laptop with me so i haven't tried the above suggestions....

BUT,  **@sonofusion82** does this mean that kubuntu will not read my external NTFS usb drive, and it must be formatted to fat32, or just that i need to mount it before it is usable

many thanks all,

---

### Post by Hobo Joe on 2007-08-16
> **sonofusion82 said:**
> yes, kubuntu has this problem with not mounting external USB NTFS partitions, FAT32 are fine.

after you figure out the the device with fdisk command above, you can mount /dev/sd??  with the mount command like
sudo mount -t auto -o umask=000 /dev/sd??  mount_point

No, that won't mount it, that will just show the drive(s) and how they are parititioned.

---

### Post by annda on 2007-08-16
1. your wireless is supported via restricted kenel drivers. in KDE you need to go to system  settings>advanced>restricted drivers and click on 'administrator mode'. now you should be able to choose the intel driver. if you don't see it listed, install linux-restricted-modules for you kernel in adept. you can find out your kernel version when you boot or by running
```
uname -r
```
in the terminal/konsole.

2. you can quickly mount the external drive using
```
pmount /dev/sdxx external_drive
```

find out xx from fdisk output. however pmount cannot use an existing mountpoint, so if you want to have your drive mounted as external_drive make sure that is doesn't exist in the /media directory (it will be temporarily created by pmount and you can access your disk there).

p.s. you can also mount the drive using sonofusion's advice:
> sudo mount -t auto -o umask=000 /dev/sd?? mount_point

but you will have to create a mountpoint in /media first.
```
sudo mkdir /media/whatever_you_want
```
if auto doesn't work, use '-t ntfs' instead.

---

### Post by tango_ninja on 2007-08-17
@annda

thanks for the pointers.

thus far I haven't yet begun to work on the wireless, but as for the external usb hd, pmount works great, but is only temporary

if i try the sudo mount command i receive an error

```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1
           missing codepage or other error
           In some cases useful info is found in syslog - try
           dmesg | tail or so

```

same error if i use **auto** or **ntfs**

I can access my data using pmount, but it would be nice to have the disk permanently accessible..

---

### Post by tango_ninja on 2007-08-17
so far none of thise has worked (for wireless or usb ntfs external)

any other ideas??

---

### Post by tango_ninja on 2007-08-19
OK I am trying to figure out the sudo mount command, I don't really understand the variables to run to mount my external hd

here is the info on the drive i want to mount (though <<sudo fdisk -l>>

```

Disk dev/sdb: 250.0 GB, 25005930016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot           Start         End              Blocks       Id          System
/dev/sdb1                    1      30401       244196001      7     HPFS/NTFS

```

---

### Post by Raptor45 on 2007-08-19
For simplcity's sake, I have two questions:

Why did you pick Kubuntu? I don't believe Ubuntu has this issue, perhaps it might be worthwhile to switch? (Note: I have not used Kubuntu, although from my experience with Xubuntu and the fact that you're seeing issues here, Ubuntu tends to be considerably more polished and less buggy. I have no gripes with KDE, but Ubuntu is the main version and thus tends to be better tested.)

Do you plan to use this on other computers? Why not reformat it to fat32 or ext3?

---

### Post by markusf21 on 2007-08-19
u could install ubuntu-desktop via synaptic. then log in to gnome and see if it is just a kde problem

---

### Post by Kitsun on 2007-08-19
Its insulting how badly supported Kubuntu is.

They bitch about how Automatix causes problems, yet a program they do support has many problems.

I mean, c'mon, compare ubuntu.org to kubuntu.org

Sry for my little rant, its just very microsoftey what the ubuntu devs are doing.

---

### Post by tango_ninja on 2007-08-19
haha you all mayvery well be right, but I like the KDE gui better than GNOME, which is really the only reason i'm using kubuntu.
i'm a linux newbie, and this was my first install, to be honest it's thus far all I know about linux and I cannot compare to anythg

you're right, I could reformat this to FAT32 but due to my nature i want to make it work this way :)

many thanks,

---

### Post by Raptor45 on 2007-08-19
> **tango_ninja said:**
> haha you all mayvery well be right, but I like the KDE gui better than GNOME, which is really the only reason i'm using kubuntu.
i'm a linux newbie, and this was my first install, to be honest it's thus far all I know about linux and I cannot compare to anythg

This seems very contradictory. How can you know you like KDE better than Gnome if you're so new to linux? Have you ever used Gnome? Upon what are you basing this judgment?

> **tango_ninja said:**
> you're right, I could reformat this to FAT32 but due to my nature i want to make it work this way 

Fair enough, I don't blame you.

---

### Post by tango_ninja on 2007-08-19
good point, It's not based upon much.
I've only heard it said that GNOME is comparable to the Mac OS GUI while KDE is the Windows equivalent

---

### Post by tango_ninja on 2007-08-19
PS what's involved in switching ? must I start from scratch again.......or can I keep ALL of my settings and configurations (i'm been customising and adding/deleting/downloading/editing for nearly a week now)

---

### Post by Raptor45 on 2007-08-19
It is possible to make the switch, but I would seriously recommend reinstalling fresh. Especially being a new user, I wouldn't recommend introducing new sources of problems. Plus, Gnome will have a completely different set of programs and settings to choose from.

---

### Post by tango_ninja on 2007-08-19
thanks all, I now have my wireless working :)

..........on to the usb HD.. i mya just reformat it in fat32 if i can't find a viable solution..

---

### Post by jordanmthomas on 2007-08-19
It seems to be down at the moment, but try going to 
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

and find the section on NTFS.  It should help you out some.

**for the record, I use Archlinux and KDE and getting my external NTFS drive to automount the way I wanted was pretty tough and troublesome.  I could mount it manually with no problem, but I ended up having to set up an entry for it in /etc/fstab so it would get auto-mounted in the right place.**

---

