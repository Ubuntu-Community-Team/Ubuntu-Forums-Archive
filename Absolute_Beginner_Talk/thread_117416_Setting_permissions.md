---
title: "Setting permissions"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by seakiwi on 2006-01-14
When I installed Ubuntu I created four partitions ...

/ 6 GB (boot)
swap 2 GB
/home 2 GB
/FAT32 - remainder of my 80 GB drive

I want to use the FAT32 partition for most of my "stuff" but I just tried to create a new folder in there and it won't let me. There is no right click option to "create new folder" and when I tried to move one from my /home directory to the FAT32 partition it told me I don't have required permissions.

How do I give myself the required permissions to do whatever I want to do in that partition? Was it something I forgot to select during the partitioning process?  :???: 

It's not a great deal of use having an empty 70 GB partition that I can't do anything in ;)

---

### Post by ed_d on 2006-01-14
try "sudo chown -R yourusername:yourusername /mountpoint of filesystem"

where asr "your username" is well the user name you log in as, and the mountpoint of file system is the name that you created for that fat disk.

---

### Post by paulmilliken on 2006-01-14
[QUOTE=seakiwi]When I installed Ubuntu I created four partitions ...

/ 6 GB (boot)
swap 2 GB
/home 2 GB
/FAT32 - remainder of my 80 GB drive

I want to use the FAT32 partition for most of my "stuff" but I just tried to create a new folder in there and it won't let me. There is no right click option to "create new folder" and when I tried to move one from my /home directory to the FAT32 partition it told me I don't have required permissions.

How do I give myself the required permissions to do whatever I want to do in that partition? Was it something I forgot to select during the partitioning process?  :???: 

It's not a great deal of use having an empty 70 GB partition that I can't do anything in ;)[/QUOTE]


Normally, to change permissions on a folder, you would use the chmod command and to change ownership you would use the chown command.  Type "man chmod" and "man chown" for details.  However, in your case, you are dealing with another partition.  It should be mounted and listed in your /etc/fstab file.  Can you post the contents of your /etc/fstab please?  Type "sudo less /etc/fstab" to see the contents or open the file with your favorite text editor and copy and paste.

Paul

---

### Post by aysiu on 2006-01-14
[QUOTE=paulmilliken]Normally, to change permissions on a folder, you would use the chmod command and to change ownership you would use the chown command.  Type "man chmod" and "man chown" for details.  However, in your case, you are dealing with another partition.  It should be mounted and listed in your /etc/fstab file.  [/QUOTE] The short tutorial:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

The long tutorial:
[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

---

### Post by seakiwi on 2006-01-14
I forgot to mention one thing ...

I have ** two** HD's in this machine. One is Windows XP Home and the other is my Ubuntu drive. The FAT 32 partition is on my Ubuntu drive, not on my Windows drive.

Not sure if that makes any difference but I figured I better mention it.

---

### Post by seakiwi on 2006-01-14
[QUOTE=paulmilliken]Normally, to change permissions on a folder, you would use the chmod command and to change ownership you would use the chown command.  Type "man chmod" and "man chown" for details.  However, in your case, you are dealing with another partition.  It should be mounted and listed in your /etc/fstab file.  Can you post the contents of your /etc/fstab please?  Type "sudo less /etc/fstab" to see the contents or open the file with your favorite text editor and copy and paste.

Paul[/QUOTE]


OK, here's my fstab contents:




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb4       /common         vfat    defaults        0       0
/dev/hdb2       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



The partition I'm referring to is the one named "common".

---

### Post by aysiu on 2006-01-14
Type these commands: ```
sudo cp /etc/fstab /etc/fstab_backup
sudo umount /common
sudo nano /etc/fstab
``` Then replace this line ```
/dev/hdb4 /common vfat defaults 0 0
``` with this one ```
/dev/hdb4 /common vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X), confirm (y), and exit (Enter). Then ```
sudo mount -a
```

---

### Post by seakiwi on 2006-01-14
OK, I tried that but now it tells me "hdb already mounted or  /common is busy"
and I still can't do anything in /common.

When I edit that fstab should the fields be space delimited or tab delimited?

---

### Post by aysiu on 2006-01-14
[QUOTE=seakiwi]OK, I tried that but now it tells me "hdb already mounted or  /common is busy"[/quote] Shouldn't be doing that if you typed in the command ```
sudo umount /common
```

> 
When I edit that fstab should the fields be space delimited or tab delimited? I don't think it matters. Just copy and paste what I gave you.

---

### Post by seakiwi on 2006-01-14
I definitely typed in the "sudo umount /common" command. I've got someone here double checking me over my shoulder, and we tried this twice just to be sure.

And copy and paste is what I did.

---

### Post by aysiu on 2006-01-14
That's weird.
Well, ```
sudo mount -a
``` is the shortcut version.
You could also try, after modifying the /etc/fstab, just rebooting the computer.

---

### Post by seakiwi on 2006-01-14
I posted a little while ago but something weird happened - I don't see it anywhere now :???: 

Anyway, to repeat what my invisible post said ...

I followed the suggestion above by ed_d and it worked. Somehow I'd missed seeing his post earlier. 

I now have ownership and permissions for my /common partition.

Thanks for everyone's help :)

---

### Post by seakiwi on 2006-01-15
[QUOTE=seakiwi]I posted a little while ago but something weird happened - I don't see it anywhere now :???: 

Anyway, to repeat what my invisible post said ...

I followed the suggestion above by ed_d and it worked. Somehow I'd missed seeing his post earlier. 

I now have ownership and permissions for my /common partition.

Thanks for everyone's help :)[/QUOTE]

This is weird. Having sorted this out yesterday, and having created a new folder (and installing something in it) I went back in there last night only to find that my folder and contents had disappeared. On closer inspection I now see that my new ownership of that /common partition has disappeared. Properties now states that "root" owns it.

The only thing I did between fixing the ownership and breaking it again, was reboot the machine ( I had to boot into Windows for something).

Why would the ownership change not have "stuck"?  This is the command I used just as ed-d suggested:

*"sudo chown -R yourusername:yourusername /mountpoint of filesystem"*

How do I make the ownership of this partition stick?:confused:

---

### Post by seakiwi on 2006-01-15
**HELP! ** :confused: 

Something is very very screwed up here. I just went to do something in /home and I no longer have ownership of that either! 

This is getting very scary ... can I fix this mess somehow or am I looking at a reinstall already? :( :( :( :(

---

