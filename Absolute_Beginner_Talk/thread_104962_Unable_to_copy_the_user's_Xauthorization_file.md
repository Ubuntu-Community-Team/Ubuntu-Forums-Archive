---
title: "Unable to copy the user's Xauthorization file"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by redgilda on 2005-12-17
Hmm

Since I installed Ubuntu a week ago I was able to run programs from the menu - System/Administration/Disks
or
System/Administration/Synaptic
etc
but now I am getting this error:
 Unable to copy the user's Xauthorization file 
so its unable to run this program as root user...

I tried searching for it here and seems like its a bug?

[http://ubuntuforums.org/showthread.php?t=21921](http://ubuntuforums.org/showthread.php?t=21921)

but why was it working before? today the only thing I tried to do is to change permissions settings for certain folders.. thats why I changed the password for root and logged in as root to try to change the permissions (which didnt work btw) but well.. now I cant run programs from the Menu..

when I try to log as root in the terminal using 'su' and then running synaptic from the terminal - it does work..

any suggestions? any comments?

a linux newbie......

---

### Post by amohanty on 2005-12-17
Can you post the output of:

> ls -l .Xauthorization

> oday the only thing I tried to do is to change permissions settings for certain folders

Can you post the **_exact_** command you used to do that?

AM

---

### Post by redgilda on 2005-12-17
hmm alright.. seems like this Xauthorization file doesnt exist even? ;-)

heres the file .Xauthority ```
 -rw-------  1 root root 119 2005-12-17 13:47 .Xauthority
```

mind you, right now, even with the permissions above - everything DOES work properly...  but i have changed and restores some many things today that I cannot account for anything... I guess I shouldnt be playing with something I have no idea about ;-)

and to change the permissions of the folders I used the command I got here:
[http://www.linuxcommand.org/lts0070.php#file_permissions](http://www.linuxcommand.org/lts0070.php#file_permissions)

chmod 666 /usr (or sth.... the whole gnome panel/menus disappeared after so I quickly changed it back...)

now things seem to be working fine, but yeah... i am starting to think that Linux is too difficult for me... *sigh*

---

### Post by amohanty on 2005-12-17
> hmm alright.. seems like this Xauthorization file doesnt exist even?


Sorry I made a typo. It is the .Xauthority file. If this the .Xauthority file of the regular user, this is very very wrong.

Do the following:

> sudo chown username:username .Xauthority
replace username with your username.

-rw------- is correct. Its just that you had the wrong owner for the file.

_Never_ _ever_ muck with the permissions in /usr especially at the folder level. Changing permissions at individual file level is ok provided _you know what you are doing_.

HTH
AM

---

### Post by bscbrit on 2005-12-17
The reason that you cannot 'see' the Xauthority file is because its name begins with a '.' - this is the perhaps the equivalent of a hidden file in Windows.  The command

ls -a filename

tells the list program to display all files that match the filename specification, even those that are normally hidden.  In Gnome (or more correctly in Nautilus), you can select View -> Show Hidden Files to see them; in your home directory you might be surprised at how many are there.  But do not delete them or change their permissions (although most of them should have your permissions as default).  They all have a purpose and making them inaccessible means that something will not work quite as intended.

---

### Post by redgilda on 2005-12-17
> **bscbrit]The reason that you cannot 'see' the Xauthority file is because its name begins with a '.'[/QUOTE]
 said:**
> _Never_ _ever_ muck with the permissions in /usr especially at the folder level. Changing permissions at individual file level is ok provided _you know what you are doing_.
yeah I know that I don't know what Im doing... but I was so curious about trying out Linux that I gave in.... ;-) many things annoy me, but its probably all because I cant configure them correctly.. like not being able to access some of my files that I have on Windows (the damn NFTS file system:P) but yeah, Ill try to be careful ;-)

Thanks!

---

### Post by amohanty on 2005-12-18
> like not being able to access some of my files that I have on Windows (the damn NFTS file system:P)

search the forums, there are tons of q&as about this. What you want is the right entry in your /etc/fstab file.

Hth
am

---

### Post by bscbrit on 2005-12-18
What is in your /etc/fstab?  Can you post a copy of it here, please?

---

### Post by redgilda on 2005-12-18
[QUOTE=bscbrit]What is in your /etc/fstab?  Can you post a copy of it here, please?[/QUOTE]
sure :)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hdb5       /media/hdb5     vfat    defaults        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by aysiu on 2005-12-18
Follow these instructions *exactly*. Open up a terminal and type in these commands.

```
sudo umount /media/hda1
sudo umount /media/hda5
sudo umount /media/hdb1
sudo umount /media/hdb5
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace your entire /etc/fstab with this instead ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222 0  0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222 0  0
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000  0 0
/dev/hdb5       /media/hdb5     vfat    iocharset=utf8,umask=000  0 0
/dev/hda8       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` Save (Control-X), confirm (y), and exit (Enter). ```
sudo mount -a
```

---

### Post by redgilda on 2005-12-18
```
redgilda@redgilda:~$ sudo umount /media/hdb1
umount: /media/hdb1: device is busy

```
what could THAT mean? should I close all the programs or something? hmm

---

### Post by redgilda on 2005-12-18
alright yeah, seems like the system hung :P (weird, I thought linux was better than windows because it was not supposed to freeze ;-)

now all works fine, I can access all the drives.. thanks!

now Im wondering how to 'share' my ubuntu stuff with windows? I did add the folder /home/redgilda into 'shared folders' (it asked me to instal SIMBA too) but I still dont see the folder when i boot into winxp...

---

### Post by amohanty on 2005-12-18
Its Samba.
Did you install it?

Also take a look at this:
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by TheDriZZle on 2008-07-24
I had the same error message. In my case the /tmp directory's permissions and ownership was somehow changed.

To fix this problem as root run:

```

chmod 1777 /tmp
chown root:root /tmp
```

This has happened twice to me now so hope this helps someone. :)

---

