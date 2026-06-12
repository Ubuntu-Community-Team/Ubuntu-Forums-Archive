---
title: "New drive, What do I do now?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by jaybmx on 2006-08-20
I have an Ubuntu system and I want to add another hard drive for media storage.
I want to be able to share the contents of the drive with all the systems on my network, mostly xp systems...
Can someone give me a quick step by step on the best method?
Im not sure how to format the drive and mount it and all that... Ive got the sharing and smb thing down, but im not sure how to set the proper permissions/ownership of the drive..
I will prolly use an older IDE drive that is currently formatted NTFS...I dont care about the data on the drive...

Also, is this might need its own post, but is there an easy way to check the stability of the new drive or to see if its got any problems?

Thank you;)

---

### Post by scxtt on 2006-08-20
i'd format it FAT32 (and if necessary use umask for permissions for /etc/fstab) ...

so put it in your box and boot up ubuntu, then use gparted to format it ...

we can handle particulars later ...

---

### Post by rck_hitokiri on 2006-08-20
you should try mounting it first then,
go to application > accessories > terminal.

make a directory in which to mount your hardrive.
code: sudo mkdir /windows (this is the mounting point)
then configure your fstab-this is your default config for your drives.

code: sudo nano /etc/fstab
it should come to this menu.:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc         proc defaults     0       0
/dev/hda1       /windows      ntfs nls=utf8,umask=0222 0        0
/dev/hdb1       / ext3        defaults,errors=remount-ro 0      1
/dev/hdb5       none          swap sw           0       0
/dev/hdc        /media/cdrom0 iso9660 ro,user,noauto    0       0
/dev/hdd1       /windows2     ntfs nls=utf8,umask=0222  0       0

if you have an ntfs file system partition try to copy /dev/hd1 or /dev/hdd1 for your ntfs config, if you are having fat32 partitions please say so so that i can post a config. thanks... cheers

---

### Post by jaybmx on 2006-08-21
OK, I installed the hard drive and formatted it to fat32 using gparted... easy enough...
then i made a directory called /MP3 to be used as the mounting point...

How do i mount it and make is read/writeable for all users?
How do I know what exactly to add to my fstab file?

Thanks!

---

### Post by huygens on 2006-08-21
> **scxtt said:**
> i'd format it FAT32

If the drive is going to be shared by Samba (SMB), the filesystem does not need to be FAT32 :)
I would rather recommend in this case a Linux native filesystem like [ext3]("http://en.wikipedia.org/wiki/Ext3") (the default), [ReiserFS]("http://en.wikipedia.org/wiki/Reiserfs"), [ Reiser4]("http://en.wikipedia.org/wiki/Reiser4") (perhaps not available...), [xfs]("http://en.wikipedia.org/wiki/Xfs") or [jfs]("http://en.wikipedia.org/wiki/JFS")... Check on Wikipedia the pros' and cons' for each...

Now to mount your partition automatically, you need to find out its name (something like /dev/hdb1 or /dev/hdc1). Then a line in the fstab like the following shall do it (assumption, the drive name is /dev/hdc1, the filesystem is ext3 a,d the mount point is /MP3)
```
 /dev/hdc1       /MP3 ext3        defaults 0 0
``` 
OK, now open a terminal and type the following to mount the new partition:
```
sudo mount /MP3
``` Now the best it to create a public folder that you will share with Samba (SMB) over the network with other computers (Windows, Linux, Mac, whatever...)
```
sudo mkdir /MP3/shared
sudo chown <your_username> /MP3/shared
sudo chmod 0755 /MP3/shared
``` With this everyone can read your files, but only the person identify as yourself over the network can modify them or create new ones. If you would like your family to modify/create files in this folder, then do this in addition to the previous:
```
sudo chgrp <your_family_group> /MP3/shared
sudo chmod g+w /MP3/shared
``` The group <your_family_group> needs to be defined in System->Administration->Users and Groups. And you and all your family accounts need to belong to this group (it does not need to be the primary group).

Then you need to share /MP3 over the network :)
Go the the "Places" menu on top of your computer screen, then select "Computer" in the listed items. You should see now your mount point MP3. Double click on it. You will there see the "shared" directory. **Right** click on it with your mouse and select "Share folder". You might be prompt to install Samba or NFS for file sharing if those packages have not yet been installed. To share files with Windows, it is recommended to use the Samba service. After validating this, a window like this should be displayed:
[[IMG]http://static.flickr.com/85/217760169_f0d9ff4db7_o.png[/IMG]]("http://www.flickr.com/photos/huygens_25/217760169/")

In “Share with”, you should select SMB which stands for the protocol name used by Microsoft for file sharing (recently Microsoft changed the name, but SMB still stick to it…) and also as a shortcut for Samba. You will get a new window like this:
[[IMG]http://static.flickr.com/90/217764768_5fc017ab80_o.png[/IMG]]("http://www.flickr.com/photos/huygens_25/217764768/")
Basically, you should only need to set a network share name in the field “Name:”, and validate your entry. You might want to have a look at the other options to tune the way your share will be available. Also, if you have changed the default Windows XP workgroup on your Windows system, it would then be recommended, to click on the “General Windows sharing settings” button and modify the “Domain / Workgroup” field to match the one you specified under Windows.
 However, if you just installed Samba during this phase you are not completly done. You should first activate Samba. This is done in the menu “System” -> “Administration” -> “Services”. There you scroll down and look for the Samba service, and you just have to activate it by checking it. Samba is now running.
 Nevertheless, you are still not ready. If you try from Windows to access your Linux box, you will see it, but strangely you cannot connect to it, eventhough you have entered the correct login and password. This is because Windows XP and Samba are configured by default to send password encrypted over the network (this was not the case with Windows 98 and earlier release!)
 On Linux, you need an additional step for each user that needs to be authenticated on the network. This step will simply add a “network user” with a encrypted password in the Samba configuration. You need to go in a terminal (menu “Applications” -> “Accessories” -> “Terminal”) and there you type the following command where you will replace *username* by your username (must be a valid Linux login).```
$ sudo smbpasswd -a *username*
``` 
This script will probably prompt you for the “sudo” password, and then it will prompt you for the SMB password. Please, set there the password you wish to enter from Windows.
 You could add this operation when creating new user, so it would become transparent for you. I do not have right in mind how to proceed, I might update this article soon, when I feel the need for this feature.
 Also, if you want to authorise a friend to access a network share but not to have a login possibility on your Linux. You need to create a Linux account for him and disallow login. This featute is hidden inside the “Advanced” tab of the User account creation window (see “System” -> “Administration” -> “Users and Groups” -> “+ Add User”). You need to select “/bin/false” for the Shell, and type “/dev/null” (without the double-quotes of course) for the home directory. In the “User Privileges” tab, deselect everything. Once this user has been created, you can perform the step, mentioned above using smbpasswd command, to create the corresponding network user. In that way, your friend will have no possible login via Gnome or a shell. But can access your shared folders.

Huygens

---

### Post by huygens on 2006-08-28
You also can use : System -> Administration -> Disks
It is a neat interface to manage hard disk partitions. The only bug I know is that it does not properly handle LVM partitions, but you probably do not use this technology.
There is a short manual on this tool here: [https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

---

