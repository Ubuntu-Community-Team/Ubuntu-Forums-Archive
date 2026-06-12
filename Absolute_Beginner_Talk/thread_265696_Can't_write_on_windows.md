---
title: "Can't write on /windows"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by ubbu on 2006-09-26
I once created the directory /windows to browse the fat32 file formatted harddisk, it ok while browsing it but no matter i type sudo nautilus and browse the content there is always a lock icon on the windows directory and can't write anything into it

While I try to change the permission setting there is a note under it saying "you are not the owner so you can't change these settings"

is there a solution for this ?

thanks in advance

---

### Post by gertmul on 2006-09-26
Can you open a terminal and type ```
ls -l /
``` to see who is the owner and what the rights are for the /windows folder?

---

### Post by ubbu on 2006-09-26
```
dr-xr-xr-x   1 root root 16384 2006-09-20 09:30 windows
```

this is what exactly lists there

---

### Post by bluefrog on 2006-09-26
it says exactly what you say. no write permission for root..

sudo chmod +w /windows

James

---

### Post by Average Joe on 2006-09-26
Alternatively, you could mount your windows partition in your /etc/fstab file with the additional options:
uid=1000,fmask=0133,dmask=0022
That will make you the owner of all files on that partition, and only you will have write access to them.

---

### Post by ubbu on 2006-09-26
wrote

sudo chmod +w /windows

and it gave

chmod: changing permissions of `/windows': Read-only file system


but still there is the lock icon and same listing when i typed ls -l /

something I miss ?

---

### Post by Omnios on 2006-09-26
whats your fstab entry.
```

sudo gedit /etc/fstab

```

 Peraonally I use 
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       

```

 Though someone stated that is not very secure but I use it for a documents drive so not to worried.

 There is also a good article on fstab in my signature

---

### Post by gertmul on 2006-09-26
What command or steps did you follow to mount the /windows folder to the FAT32 partition?

---

### Post by ubbu on 2006-09-26
> **gertmul said:**
> What command or steps did you follow to mount the /windows folder to the FAT32 partition?

1 - sudo mkdir /windows
2 - sudo cp /etc/fstab /etc/fstab_backup.
3 - sudo nano /etc/fstab
4 - i changed the drive line to " dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0"
5- sudo umount /dev/hdb1
sudo mkdir /fat_files
6 - added this line to fstab " /dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0"
7 - sudo mount -a

that was it
any wrong step with this procedure ?

---

### Post by Ben Sprinkle on 2006-09-26
> **Goat Spirit said:**
> Any linux **cannot** write to any NTFS system (WinXP), this may be why your having trouble. There may be distros or apps that can in the future but as of now they can't.

Sorry. :(

---

### Post by Bachstelze on 2006-09-26
[Wrong](http://www.ubuntuforums.org/showthread.php?t=217009).

---

### Post by gertmul on 2006-09-26
yes according to your line:

4 - i changed the drive line to " dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0"

You are trying to use an ntfs partition for /windows and not FAT32

---

### Post by Ben Sprinkle on 2006-09-26
Would you know how then? I have been told numorus times that it's not possible.

---

### Post by ubbu on 2006-09-27
> **gertmul said:**
> yes according to your line:

4 - i changed the drive line to " dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0"

You are trying to use an ntfs partition for /windows and not FAT32

Changed ntfs to FAT32 in that line but appearantly nothing changed.

---

### Post by Medieval_Creations on 2006-09-27
If I'm following the thread right the partition you are trying to mount is NTFS not FAT32.  The Linux kernel does not have native read/write capabilities for NTFS partitions so you have to get a little more creative.

The best workaround that I have come across is ntfs-3g.

Here is the HOWTO: thread  -  [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

but here are the steps in a nutshell.

1.) First you will need to add a repository to your source.list. Open a terminal and type:
	gksu gedit /etc/apt/sources.list

2.) At the end of the file, just add the following:
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main

3.) Save & Exit

4.) Now Update and Install
	sudo apt-get update
	sudo apt-get upgrade
            sudo apt-get install ntfs-3g

5.) Unmount the NTFS partition if needed

6.) Here is an example of now you will mount the NTFS partition using ntfs-3g
	sudo ntfs-3g /dev/<your partition> /mnt/<folder name>
		Here an example with my setup:
			sudo ntfs-3g /dev/hdb6/ /mnt/Storage_NTFS/

7.) You can unmount the partition normally
	sudo umount /mnt/Storage_NTFS


One side note is that you have to be root to write to the NTFS partition. So I do alot of my file transfers to my NTFS partition in a terminal.
I hope this helps...

** Note: that when working with NTFS it is all still classified as “testing” and there is always the chance of corrupting data. **

---

