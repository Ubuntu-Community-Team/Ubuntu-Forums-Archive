---
title: "External Hard Drive Permissions ..Help!"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by infiniteshadow on 2007-10-06
I have got an Internal HDD in an External encloser. It is a Maxtor 200 gig ATA hard drive. It works perfectly in windows but in Ubuntu it only reads. I cant change / rename folders  add files or delete older files. Btw since i installed beryl (sigh..) the Login Manager says...Could not access Configuration File (custom.conf) 


i also have NTFS configuration tool installed....do i know how to use it..................nope :P

---

### Post by fotno on 2007-10-06
NTFS is your problem.I'm hearing that Gutsy will have a repair for that problem.One can only hope.

---

### Post by taurus on 2007-10-06
You need to use ntfs-3g driver instead of default ntfs if you want to write to ntfs filesystem.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by infiniteshadow on 2007-10-14
Can i get a BUMP-DE-HUMP DO BAP BUMP DE HUMP
red hot chili peppers

---

### Post by infiniteshadow on 2007-10-23
bump....

---

### Post by Vansinnesvisan on 2007-10-23
You could try mounting it with read/write permissions.
```
mount /dev/<your drive> /mnt/<where it's mounted> -t ntfs-3g -rw -o umask=0000,force
```

/etc/fstab would need to be edited to make that permanent. 

Just an idea if nothing else.

---

### Post by Sand Lee on 2007-10-23
**Use this method if you probably won't have a person maliciously attack your computer in person (like me).**
[LIST=1]
[*]Press Alt+F2 and type "gksudo nautilus" (sans quotes) -- this lets you use the filemanager as a superuser
[*]Click Run, type your password when asked, and press enter
[*]Access the folder where your Ext HD is mounted (/media?)
[*]Right click the HD and select properties
[*]Click the Permissions tab
[*]Change Folder Access for all three sections to Create and delete files
[/LIST]
Now it should work. I used this exact method to access my /media/data and /media/test partitions after installing Gutsy.

---

### Post by Qwerty_ on 2007-10-23
Did you follow the instructions in the link provided above?

That will confiqure your Ubuntu to beable to access the NTFS partitions on a drive.

```
sudo apt-get install ntfs-config
```

Once it has installed run

```
sudo ntfs-config
```

Select your required settings and you should be good to go.

---

