---
title: "Permissions - Main HD &amp; External USB"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by schnigga on 2007-01-07
Hi, I hope this isn't looked upon as an uninformed posting, I've tried so hard.

First:
My main hard drive, a Western Digital 60GB, which prior to install was nuked with DBAN. Everything went smoothly including the install from the live CD.  (Dapper by the way.) Everything seems to work, I have done absolutely no customizing, every "single" option is default. I am trying to install an application, (Songbird.) I can extract, sort of, to a folder. By this I mean accidently. It says I don't have permissions to rename, delete, or move. I just want to be able to have full access from bootup. I have tried searching google, none of the methods work, chmod, chown, sudo -i, (I think that is one?) After looking through the forums, I see fstab and similar commands. I looked but am unsure of how to use them, I don't want to mess up.

Second: External USB hard drive, same as above, see and able to copy files, but not full access. When I plug it in, it automatically recognizes and places an icon on my desktop. Open it, copy to Desktop, but no paste, move, or delete. Do I need to mount? fstab looked like the likely way to go but I am afraid of messing up. Every forum I read, or google search I view is similar, but not exactly  like mine. I am at a dead end. I have terminal'd myself brain dead ](*,) Thanks in advance if anybody has any ideas. (Oh, I have also been looking at NTFS-3G, but it's a driver and I thought maybe I just needed to set permissions or something. Example of setting permissions with sudo as I've read:

chris@chris-desktop:~$ cd /opt
chris@chris-desktop:/opt$ chmod 777 Songbird.tar.gz
chmod: changing permissions of `Songbird.tar.gz': Operation not permitted
chris@chris-desktop:/opt$

Thanks,
Chris

---

### Post by taurus on 2007-01-07
```
**sudo** chmod 777 Songbird.tar.gz
**sudo** tar xvzf Songbird.tar.gzp
```

---

### Post by schnigga on 2007-01-07
Thanks for the input Taurus. The command went through fine, but I got a "popup" error message...

"/opt/Songbi...i686.tar.gz" cannot be moved because you do not have permissions to change it or its parent folder.

Didn't seem to work. Mainly I am trying to achieve the right click "Send to trash, Rename, and Cut." Is there a way to apply this to the whole drive? Any other ideas?

Thanks,
Chris

---

### Post by aysiu on 2007-01-07
I wrote a script for installing Songbird:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

That should make your life easier. If you don't want to make your life easier but just want to learn the commands, you can open the script with a text editor and see what commands it uses.

---

### Post by taurus on 2007-01-07
If you want to remove it, try using the sudo again.

```
sudo rm *.gz
```

---

### Post by schnigga on 2007-01-07
Thanks taurus, I was able to remove them, one more thing I learned! And thanks aysiu, that is a wonderful script you wrote. I will go through the text editor and see what I can learn. Thanks again.

---

### Post by schnigga on 2007-01-07
Oh... I forgot :) the permissions thing. I need to get r/w/x privileges on both my main HD and my external USB, any ideas?

---

### Post by Frank Golden on 2007-01-07
> **schnigga said:**
> Oh... I forgot :) the permissions thing. I need to get r/w/x privileges on both my main HD and my external USB, any ideas?

I'm not sure you want full read/write/execute priveleges on your main drive. Not
secure. Plus some files and folders need to remain the way they are (permissionwise) at boot or you will break Ubuntu. 

You could use the terminal command [COLOR="Red"]gkdudo nautilus / [/COLOR] this will open your filesystem (your main drive) in nautilus, a file browser, as root. You will have
full read/write/execute and (destroy if you don't know what you are doing) your file system. When using the above method be careful. Your chances of messing up Ubuntu
are much greater.

If your external drive is Fat32 it should already be read/write if it installs automatically.
If NTFS you need to install a program to facilitate writing to NTFS from Linux.
These programs are "experimental". Many people say they work well. I myself won't
use them. My Ubuntu install shares a HDD with XP Pro.  My XP is NTFS so I can access it
from Ubuntu but I can't write to it thereby keeping me from screwing up my XP install.
I keep a separate partition Fat32 for sharing data between the two OS's.
I also maintain a external drive Fat32 for the same reason. I know Fat32 isn't ideal
(4GB file size limitation and prone to fragmentation) but I can live with them.

---

### Post by schnigga on 2007-01-07
Thanks for the tip for not making my main drive r/w/x. As for the external, it's strictly for sharing, but I can't create folders, can't cut, copy, delete files. It's FAT32 (I thought it was NTFS, sorry for the confusion), and I can see everything. Reason behind doing this is I want to be able to organize the contents. Any ideas.

---

### Post by Frank Golden on 2007-01-07
> **schnigga said:**
> Thanks for the tip for not making my main drive r/w/x. As for the external, it's strictly for sharing, but I can't create folders, can't cut, copy, delete files. It's FAT32 (I thought it was NTFS, sorry for the confusion), and I can see everything. Reason behind doing this is I want to be able to organize the contents. Any ideas.
Try the technique I outlined above [COLOR="Red"]gksudo nautilus /[/COLOR]
and navigate to  /media/<name of your external drive>. You should be able to do anything you want there. Does it mount automatically when plugged in? Do you have a 
desktop icon?

---

### Post by Frank Golden on 2007-01-08
> **schnigga said:**
> Thanks for the tip for not making my main drive r/w/x. As for the external, it's strictly for sharing, but I can't create folders, can't cut, copy, delete files. It's FAT32 (I thought it was NTFS, sorry for the confusion), and I can see everything. Reason behind doing this is I want to be able to organize the contents. Any ideas.
Try the technique I outlined above [COLOR="Red"]gksudo nautilus /[/COLOR]
and navigate to  /media/<name of your external drive>. You should be able to do anything you want there. Does it mount automatically when plugged in? Do you have a 
desktop icon?

See the following info about mounting file systems (drives are file systems as far as Linux is concerned).

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

When I plug in my external drives (if they are Fat32) they are mounted automatically
read/write/execute with a icon on desktop. I don't understand why yours won't.
Maybe someone else here can help with this.
You should be able to chmod the drive to give you full permissions. I don't know the command or whether it will be persistent.

I personally have created a panel launcher using the above command to allow me 
r/w/x access when I need it temporarily. Even if you have nautilus set for single click
and the option to create a right click entry to directly delete an item you have to reset those options in gksudo nautilus /. Not really a bad thing, keeps you from really deleting
stuff. Anything deleted will go to trash bin.

---

### Post by schnigga on 2007-01-08
Thanks for the info. Yes, when I plug it in (USB). It automatically mounts and throws on a desktop icon and I can view the files, but read only access. I would like to just have r/w/x when it auto mounts rather than go through the [ gksudo nautilus / ] method you mentioned. I have learned how to access the root using that method now, BTW thanks, it makes things so easy. But is there a way for it to auto mount with full access?

---

### Post by Frank Golden on 2007-01-08
> **schnigga said:**
> Thanks for the info. Yes, when I plug it in (USB). It automatically mounts and throws on a desktop icon and I can view the files, but read only access. I would like to just have r/w/x when it auto mounts rather than go through the [ gksudo nautilus / ] method you mentioned. I have learned how to access the root using that method now, BTW thanks, it makes things so easy. But is there a way for it to auto mount with full access?
Ok schnigga, lets try this in a terminal

```
[COLOR="Red"]sudo fdisk -l[/COLOR]
``` please post the results so I know what you system is calling your external drive.

and


```
[COLOR="red"]gedit /etc/fstab[/COLOR]
``` so I can see if you have an entry there for your external drive. Please post also.

I think I you hilite the text and right click and copy. You can paste it to your post.

The first command querrys your computer for drive info, make sure your external drive is connected for this. The second command displays your fstab file.

---

### Post by Zaphod on 2007-01-10
Hi 

Im having the same trouble as schnigga .

I have an external NTFS usb device that autmounts but I have no write access. Can open all files ...

/dev/sda1               1       24321   195358401    7  HPFS/NTFS

I tried adding this line in Fstab

/dev/sda1    /media/TV   ntfs-3g    defaults,locale=en_US.utf8    0    0

then "sudo mount -a"

Then I get this error in X when trying open the drive "mount: only root can mount /dev/sda1 on /media/tv"

:-k  I know im doing something wrong here

---

### Post by Frank Golden on 2007-01-10
> **Zaphod said:**
> Hi 

Im having the same trouble as schnigga .

I have an external NTFS usb device that autmounts but I have no write access. Can open all files ...

/dev/sda1               1       24321   195358401    7  HPFS/NTFS

I tried adding this line in Fstab

/dev/sda1    /media/TV   ntfs-3g    defaults,locale=en_US.utf8    0    0

then "sudo mount -a"

Then I get this error in X when trying open the drive "mount: only root can mount /dev/sda1 on /media/tv"

:-k  I know im doing something wrong here
You can't write to NTFS in Linux unless you use a third party program to allow write access.
There are a few out there. The problem is NTFS is closed source and very complex.
Some folks have been reverse engineering, hence the programs available. They are experimental.
Use at your own risk. You could render your drive unreadable. Having said that I can't point you to any of these programs since I have no desire to write to my NTFS drives. I look at this as a good thing because I can't mess up my NTFS volumes. My Ubuntu shares a drive with XP Pro and I allow my XP partition to mount and provide an icon on the desktop.
It is of course read only but I like it that way. If I need to share I have a Fat32 partition
on this drive that mounts and provides a desktop icon. I can write to this volume.

See below

[http://www.google.com/search?sourceid=navclient&aq=t&ie=UTF-8&rlz=1T4GGLR_en___US203&q=write+to+ntfs+in+linux](http://www.google.com/search?sourceid=navclient&aq=t&ie=UTF-8&rlz=1T4GGLR_en___US203&q=write+to+ntfs+in+linux)


EDIT: I see, from looking at your fstab entry more closely that you are using one of these third party programs. Nevermind.
Sorry I could't be more help.

---

### Post by Zaphod on 2007-01-11
Thanks for your input tough 

I already have NTFS drive that is working in my computer it's just the external one that I'm having troubles with ....

I'll keep reading and trying things:-k

---

