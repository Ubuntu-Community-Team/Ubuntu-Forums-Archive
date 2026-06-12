---
title: "Ubuntu Sharing files with windows"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by JJHughes57 on 2006-06-04
I just started using Ubuntu and am trying to set up my desktop to share files over the network. Well I created folders and logins and can access files from the desktop but can not write to any of the folder. I have checked all of them and they all have writable = yes. Still every time I try to write I get the "Access is Denied"

Can anyone offer some idea's for me?

---

### Post by NiceGuy on 2006-06-04
Just to clarify, is it that you can't write to the shared folders remotely or you can't write to them at all?

---

### Post by JJHughes57 on 2006-06-04
I just figured out that when the system creats the folder it creats them with the owner being 'root' so I can not modify any of the contents of the folder. How do I stop it from doing this? Or do I just have to create the folder first then manualy select it for sharing?

---

### Post by Poirot on 2006-06-04
I think you might need to look at the file system table (/etc/fstab), the various settings in that file determine whether partitions are mounted as read-only etc.

You will need to open the file using sudo to edit its contents.
```
sudo gedit /etc/fstab
```
Make sure you back it up just in case.

This is what mine looks like.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext2    defaults,errors=remount-ro 0       1
/dev/sda2       /media/datashare      vfat    umask=000        0       0
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```
I share my sda2 drive (fat32), it's mounted as 'datashare' in /media so it appears on the desktop and in nautilus as a separate drive. The umask=000 setting gives everyone write access, other numbers produce different results. Ideally I would only give write access to my own user and give everyone else read only access but I haven't worked that out yet.

---

### Post by NiceGuy on 2006-06-04
Ah... I thought that might be the problem. ;)

Right first off some linux basics,

On a linux system a user only has 'native' permissions to write to his/her home folder. The idea behind this is so that you (or anyone else for that matter) can't acidentally do any damage to the system. So the easy way to solve your problem is to create the folder you want to share in your home folder.

You can do this either by the gui (ie rightclick > new folder etc.etc) or by the command:

```
mkdir newfolder
```

However if you want to create a folder in another part of the system we need to do something a bit different.

Now this is a bit of an aside but important. You may or may not have heard of the root user. The root user is a special user who has complete access to the entire system. In ubuntu the root user is by default disabled (well you cant log in as root anyway), this is for a number of reasons I won't go into right now but its a good thing! Any way because root has been disabled we need to use the sudo command - sudo basically means 'super user'. I tend to think of it as being temporarily root.

Right back to the plot.

If you wanted to make the folder say...

/home/public

you would have to do it as root (or in our case using the sudo command).

NB: this is because you only have native write access you your users home folder NOT the home folder its self.

To make this folder you would issue the command:

```
sudo mkdir /home/public
```

(you probably did something like this to make your folders). Note that because you used the sudo command it was like root created the folder not your user. That's why your user doesn't have write access to it. 

However you can change who owns the folder by using the chown command!

To do this you would type:

```
sudo chown yourusername /home/public 
```

Hope that helps!

---

### Post by NiceGuy on 2006-06-04
I've just thought, if you have more than one user on your system you might not want to change ownership of the folder but just allow everyone to read and write to it. To do this you would use the chmod command.

eg. ```
sudo chmod 777 /home/public
```

what the 777 bit means is that the folder can be read by and written to by everyone.

---

### Post by NiceGuy on 2006-06-04
[QUOTE=Poirot] Ideally I would only give write access to my own user and give everyone else read only access but I haven't worked that out yet.[/QUOTE]

Poirot, If you want to do that then change the sda2 line to say:

```
/dev/sda2       /media/datashare      vfat    uid=1000,gid=1000        0       0
```

ps. I'm assuming your the first user on your system. If not run

```
 id **yourusername** 
``` to findout your user id (uid) and group id (gid). For more info look at: [http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS)]("http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS)")

---

### Post by Poirot on 2006-06-05
Thanks NiceGuy.

---

