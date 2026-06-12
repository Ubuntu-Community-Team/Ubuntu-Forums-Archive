---
title: "no fat32"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by hellfried on 2006-04-15
ok so this i what i want to do. basically i want one particular partition on my hd which i had formatted earlier with fat32. i have some files on it that i would like to read and write to in ubuntu. i have winxp on one partition, the particular partition in question, followed by the linux partititon and lastly one ntfs partition which i have already mounted and can see within the mnt folder as ntfs1 (i can't for the life of me remember where i got instructions from!).

my progress so far:
i have managed to mount the windows partition on reboot following tips from this link - [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

i tried going through the same steps for the particular partition (fat32) but came back with an error message and i had to revert back to my previously backed up fstab file. i noticed that i do not have a fat32 entry in my fstab file! it had mysteriously disappeared (maybe not that mysterious seeing that i have been mucking around with it so much lately - see attachment). i would like to auto-mount the fat32 partition like how i did with my windows partition. any help would be appreciated!

i have also included a jpg of what it looks like from partitionmagic winthin winxp. i created the fat32 partiton using gparted.

---

### Post by Princey on 2006-04-15
[QUOTE=hellfried]ok so this i what i want to do. basically i want one particular partition on my hd which i had formatted earlier with fat32. i have some files on it that i would like to read and write to in ubuntu. i have winxp on one partition, the particular partition in question, followed by the linux partititon and lastly one ntfs partition which i have already mounted and can see within the mnt folder as ntfs1 (i can't for the life of me remember where i got instructions from!).

my progress so far:
i have managed to mount the windows partition on reboot following tips from this link - [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

i tried going through the same steps for the particular partition (fat32) but came back with an error message and i had to revert back to my previously backed up fstab file. i noticed that i do not have a fat32 entry in my fstab file! it had mysteriously disappeared (maybe not that mysterious seeing that i have been mucking around with it so much lately - see attachment). i would like to auto-mount the fat32 partition like how i did with my windows partition. any help would be appreciated!

i have also included a jpg of what it looks like from partitionmagic winthin winxp. i created the fat32 partiton using gparted.[/QUOTE]


What exactly are your error messages? I took a look at your fstab and see no reference to your FAT32 partition you talk about. Can you give the output of > sudo fdisk -l

---

### Post by hellfried on 2006-04-15
see attachment. if i am not mistaken it should be sda5 that i am trying to get at.

---

### Post by plors on 2006-04-16
hi,

I guess you have used a rather old gparted which doesn't set the partitiontype correctly. That way some apps (or windows) might get confused. Use a more recent gparted to solve this ([http://gparted.sourceforge.net]("http://gparted.sourceforge.net"))

good luck :D 

PS. shame on you for attaching a file in .doc format. The most important thing about OSS is not about superior quality, but about FREEDOM, and the closed .doc format has nothing to do with that. 
Please read [http://www.gnu.org/philosophy/no-word-attachments.html]("http://www.gnu.org/philosophy/no-word-attachments.html"), it's quite interesting ;)

---

### Post by Princey on 2006-04-16
[QUOTE=hellfried]see attachment. if i am not mistaken it should be sda5 that i am trying to get at.[/QUOTE]

I'm sorry, but I didn't see any attachment though it said so. Can't you paste the contents in the post? Use the quote function to paste the contents. It's available while you type your post in the furum, it's the icon under the right arrow.

---

### Post by hellfried on 2006-04-16
[QUOTE=Princey]I'm sorry, but I didn't see any attachment though it said so. Can't you paste the contents in the post? Use the quote function to paste the contents. It's available while you type your post in the furum, it's the icon under the right arrow.[/QUOTE]

sorry i can't seem to do anything with the icon with the blue arrow. when i click on it some orange goo appears across it. when i click on the 'quick reply' icon it brings me to another page where i can type my reply with your post quoted.

i have taken a screen capture of terminal instead.

---

### Post by Princey on 2006-04-16
[QUOTE=hellfried]sorry i can't seem to do anything with the icon with the blue arrow. when i click on it some orange goo appears across it. when i click on the 'quick reply' icon it brings me to another page where i can type my reply with your post quoted.

i have taken a screen capture of terminal instead.[/QUOTE]

it's not the blue arrow, the one under it that looks like a notepad. I still can't see attachments through here.

---

### Post by Sutekh on 2006-04-16
Based on your screenshot of fdisk and the contents of the fstab, you need to edit it to include a line for your FAT partition.

First you should backup your current fstab becuase you know it works.  Then add a line like this to it
```
/dev/sda5   /media/fat_files   vfat   iocharset=utf8,umask=000   0   0
```
Then save the file and create the mount folder for the partition
```
sudo mkdir /media/fat_files
```
Of course you can use anything you like /media/fat_files is just and example

Finally mount the FAT partition with
```
sudo mount /media/fat_files
```or remount all the partitions in the fstab with```
sudo mount -a
```

---

### Post by hellfried on 2006-04-17
if you take a look at my first post where i included a screen capture of partitionmagic in winxp, you will notice that my f drive (the fat32 partition that i was refering to) is of type 07. no where does it say that it is of the type fat32. could this be because i used gparted? another thing is if you take a look at the fdisk, you will see that sda5 is now a ntfs partition. i swear that i made it fat32 with gparted before this! anyways i am now thinking of using the live gparted cd that i just d/loaded this morning to delete the partition and reformat it as fat32. following this i will mount it per your instructions. wish me luck!

---

### Post by Sutekh on 2006-04-17
I overlooked that the partition wasn't FAT32, I just assumed it was #-o 

It could be a GParted problem.  Type 07 partitions should be NTFS, and type 0B partitions should be FAT32.  I don't know why PM has this confused.  Maybe there is a problem with the partition.

---

### Post by hellfried on 2006-04-18
success!! i now have sda5 mounted on my desktop. thanks guys!

---

### Post by Sutekh on 2006-04-18
I'm glad its working now, well done!

---

