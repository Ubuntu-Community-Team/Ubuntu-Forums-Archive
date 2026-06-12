---
title: "Mounting a shared windows folder on 5.10"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by seinn on 2005-11-28
I have installed and been exploring Ubuntu for the past few days. I love it. However I have one problem, I need to mount a shared folder from win2k3.

I can browse to the folder and open documents etc which is good. But what I am looking to do is that when I start up ubuntu it will mount this folder automatically, so I can browse it from OO etc.

the folder location is on smb://windows/shared

How do I get it to mount automatically? Any help would be greatly appreciated.

Thanks

---

### Post by seinn on 2005-11-28
Anyone able to help me out here?

---

### Post by gord on 2005-11-28
the only thing that spings to mind is to use a symbolic link to the directory in your home directory 
ln -s smb://windows/shared


i have absolutly no idea if that would work though

---

### Post by akniss on 2005-11-28
[QUOTE=seinn]How do I get it to mount automatically? [/QUOTE]

Click on the Help icon on your desktop, then choose Ubuntu 5.10 Starter Guide.  In the left pane there is a Windows Partitions menu item.  This should have all the info you need.  Below is the section devoted to NTFS.  There are modifications in the guide for FAT as well.


[QUOTE=Ubuntu 5.10 Starter Guide]How do I mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

    Assuming that /dev/hda1 is the location of the Windows partition (NTFS) and the local mount folder is: /media/windows

       1. Read How do I check disk space and view the partition table?
       2.```
sudo mkdir /media/windows 
		sudo cp /etc/fstab /etc/fstab_backup 
		sudo gedit /etc/fstab
```

       3. Append the following line at the end of file

/dev/hda1 /media/windows ntfs umask=0222 0 0

       4. Save the edited file (sample/fstab_automountntfs)
       5. Read How do I remount /etc/fstab without rebooting? 

[/QUOTE]

---

### Post by GoldBuggie on 2005-11-28
To get it to mount automatically tou will need to add a line to your fstab file.
```

sudo kate /etc/fstab
``` 
Add this line(change relevent parts to your networkspecs) ```
//smbserver/sharename /home/<YOUR HOME DIRECTORY NAME>/<MOUNTPOINT DIRECTORY> smbfs uid=<LINUXUSERID>,gid=<LINUXUSERGROUPID>,username=<WINDOWSUSERNAME>,password=<WINDOWSPASSWORD> 0 0
``` Then create the directory whee you want the share to mount.
```

mkdir <MOUNTPOINT DIRECTORY>
``` 
To get the correct <LINUXUSERID> and <LINUXUSERGROUPID> do a ```
id
``` and get the numbers for your user.

Then to remount the shares in fstab without rebooting do a
```
sudo mount -a
```. Now you should have your windows share in [I]~/<MOUNTPOINT DIRECTORY>

hmmm..maybe I should make a good howto from this
[/I]

---

### Post by Jade Robbins on 2005-11-29
don't forget

> sudo apt-get install smbfs

otherwise you'll get an error when you sudo mount -a

---

### Post by seinn on 2005-11-30
Thanks Guys for all this info. I will try that out once I get back to the office next week. 

May be back if I have no luck.

---

### Post by seinn on 2005-12-16
Hi Folks

I have tried the above. GoldBuggie's solution nearly works for me. I now have the shared folder mounting on the desktop. However when i try to open it it tells me that  I do not have permssion, ie ls: .: Permission denied

The windows server has all the right settings etc set up. And when I get properties on the mounted shared folder they are all set to off.

any suggestions?

---

### Post by GoldBuggie on 2005-12-16
try and add the option in bold to the fstab line


//smb /mount smbfs **defaults,**uid=<>,gid=<L>,username=<>,password=<> 0 0

If you want to see what this option implies do a *man mount* in konsole

---

### Post by KermitJr on 2005-12-16
try umask=000

KJ

---

### Post by KermitJr on 2005-12-16
try umask=000

KJ

---

### Post by seinn on 2005-12-16
Sorry guys I am a bit confused by the last 2 posts. Here is my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

//shared/Public /home/me/Desktop/Public smbfs uid=1000(me),gid=1000(me),username=me,password=ball23 0 0

where am i supposed to add those lines? Sorry about this but I am new to all  this.

Thanks

---

### Post by GoldBuggie on 2005-12-16
Before adding the options that you were presented try and change your current line
```

//shared/Public /home/me/Desktop/Public smbfs uid=1000(me),gid=1000(me),username=me,password=ball23 0 0
```[SIZE=2]
[/SIZE]
into
```
//shared/Public /home/me/Desktop/Public smbfs uid=1000,gid=1000,username=me,password=ball23 0 0
``` 
Since having the paranthesis is hmm...don't think it will work. So try that first. Remember to do a **sudo mount -a** after saving fstab

Then if that doesn't work change the same line into
```
//shared/Public /home/me/Desktop/Public smbfs defaults,uid=1000,gid=1000,username=me,password=ball23,umask=000 0 0
``` 
[SIZE=2]
[/SIZE]

---

### Post by thezerogroup on 2005-12-16
Try LinNeighborhood, it a samba GUI tool. . . very nice. 

```
sudo apt-get install LinNeighborhood
```

---

### Post by seinn on 2005-12-20
Still having no luck. I have tried everything and to no joy. Just to make sure it isn't a server side problem, I installed Xandros linux and it just worked. You select network, then browse to the windows server and click mount this partition. Only thing with Xandros is that it is not as quick as Ubuntu and is more difficult to navigate. 

I thought Ubuntu was supposed to be linux for the Human Being, one would have thought that networking would be easier. Anyway do you have any other suggestions on how I could get this to work. It still says permission denied to me, even with all the unmask commands etc.

Your help is appreciated

---

### Post by n0ah on 2005-12-21
No promises.. but I built a little script to mount my drives because I dislike typing my password to mount while booting..

mountWinShares.sh
--
```

#!/bin/sh

#mount windows shares

clear
echo "Mounting.."
sudo mount //192.168.1.55/Shared /mnt/WIN/shared -o umask=0777,fmask=0777 && sudo mount //192.168.1.55/Websites /mnt/WIN/websites -o umask=0777,fmask=0777
mount | grep ".1.55"
echo "Ok, Done!"
sleep 2s && exit

```

gotta run it from command line so far
> bash mountWinShares.sh

hope it helps maybe (i've been having a bitch of a time trying to get it working on one of my computers atm though)

--Derek

---

### Post by darth_vector on 2005-12-21
if you dont have permission to browse the directory, fire up the terminal and

sudo nautilus

then you can browse anything. if you dont have a addressbar by default just hit Alt-d to get one.

---

### Post by scole on 2005-12-21
The simplest way is to get a decent flash drive and plug it in. If it is fat win and ubuntu will detect it avoiding all this trouble

---

### Post by seinn on 2005-12-22
Scole While that would be a simple aqnswer it wont help, as its a networked server and 10 of my staff access the files. Hence why I am trying to get the shred folder to mount on the desktop, just as it is on the windows and mac pc's.

I wonder why Ubuntu doesn't have such a basic requirement built in, surely these guys woould know many people would want to do this.

---

