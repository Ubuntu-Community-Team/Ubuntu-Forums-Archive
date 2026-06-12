---
title: "permissions on 2 external NTFS firewire hard drives"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by attak on 2007-05-27
i just downloaded the newest version of ubuntu studio and installed it with no problems.  i have 2 hard drives, both of them fire wire, that i had been using with XP on my laptop.  both drives are NTFS.  i want to keep them NTFS because i have xp installed on another partition on my internal harddrive.  when i right click and go to properties it says that the owner is root.  i cannot write any data on my drives so what i would like to know is how i can change this so i could read/write data as i normally would in windows.  i have been browsing through the forums trying to figure this out but i haven't had any luck.  i am REALLY new to linux so i don't really know what to do.

any help would be greatly appreciated.

---

### Post by ahaurw01 on 2007-05-27
You'll need to install some things to allow your compy to write to NTFS. In a terminal:
```
sudo apt-get install ntfs-3g libntfs-3g0 
```
Then,
```
sudo fdisk -l
```
Find which disk looks like your external drive and remember the name it has (ie my internal hard drive is /dev/sda1 through sda7 and my external drive is /dev/sdb1)

```
sudo gedit /etc/fstab
```
add this line to the end of the file:
```
/dev/XXXX   /media/YYYY   ntfs-3g  defaults,locale=en_US.utf8    0    0
```
replacing XXXX with the name of your external drive (in my case it'd be sdb1) and YYYY with whatever your heart desires (this is the name of the folder your external drive will be mounted to).
Add similar lines to the /etc/fstab file for any external drives you have. If you're scared about screwing up the fstab file, you can create a backup before you begin:
```
sudo cp /etc/fstab /etc/fstab_bk
```


 The only thing is that your external drives won't automount when plugging them in after booting. I think you'd still be able to ```
sudo mount -a 
```  to mount your drives after booting.

After doing all of the above steps, restart your computer and hopefully you'll be able to write to those ntfs drives. Post back if it didn't work.

Regards
aaron

---

### Post by gn2 on 2007-05-27
Alternatively go to [www.getautomatix.com](www.getautomatix.com) install Automatix, and use the Auto-Mounter listed in Miscellaneous.

It auto-mounts NTFS drives/partitions and makes them writeable. Automatically.

---

### Post by ahaurw01 on 2007-05-27
That is an option. Although I do think it's important to know what's going on when you change hard drive interactions significantly and also what caveats are present. Thanks gn2

---

### Post by attak on 2007-05-28
after typing in this:

sudo apt-get install ntfs-3g libntfs-3g0

i get this:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


i also tried going to the getautomatix site and installing the program.  when i install the automount NTFS program i get an apt based error.

help please?

---

### Post by Inxsible on 2007-05-28
Try this :

Go to Applications -- > Add/Remove 

Search for 'ntfs' (without quotes) It should show something called NTFS Configuration Tool. Check mark it for installation. After that, it will create an entry under Applications --> System Tools --> NTFS Configuration Tool.

Click on it and select read/write access to internal and external drives.

Once you have done that, to mount the drives you need to do this
For internal drives :
same procedure as listed by above poster

For external drives:
```

sudo pmount /dev/XXXX <Mount Point>

eg sudo pmount /dev/sdb1 MyData

```

This will create a folder called MyData under /media. It will also automount everytime you connect the drive

Note: if you have an existing folder called MyData under /media, the above wont work. pmount requires that you create the folder using the above command.

Hope that helps !!

---

