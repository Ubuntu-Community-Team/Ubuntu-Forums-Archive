---
title: "Accessinng a User's OSX files while using Ubuntu?"
date: 2007-09-18
forum: Apple PPC Users
---

### Post by Rev4n on 2007-09-18
I'm really new to Linux and I just successfully (I think?) Installed both OSX and Linux on the same PPC iBook.  Everything's working swimmingly, except that all of the User-specific files from OSX (Music, Movies, Documents, etc) are all locked down when I try to browse to them in Linux.  I know in OSX it's just a matter of logging in the correct account, but I guess I don't know how to do that across-OS.

Is there any way for me to access my music files and such that are stored in my User account on the OSX partition?

---

### Post by simonn on 2007-09-18
The problem is that the numeric UID (user id) and GID (group id) of your Linux and OSX users do not match. 

In linux if you do the following where [username] is your user name:
```

grep [username] /etc/passwd

```

You will see something like:
```

[username]:x:1000:1000:[Full Name],,,,:/home/si:/bin/bash

```

The 1000s are the UID and GID respectively. 

When in linux, the easiest way to determine your OSX user's UID and GID is (where [username] is the OSX user's user name):
```

ls -n [path of mounted HFS+ partition]/Users/[username]

```

Now, the problem is that Ubuntu considers UIDs >= 1000 to be actual users, rather than user used to run processes, but OSX UIDs >= 500 for the same. Therefore it is probably easier in the long run to change the UID in OSX to be = to the UID in Ubuntu.

See "To change your UID/GID on your mac" here [http://www.eecs.umich.edu/dco/help/NFSMac.htm](http://www.eecs.umich.edu/dco/help/NFSMac.htm).

However, I would suggest that you create another admin user in OSX before doing this as there is the potential to lock yourself out. You can remove the user after you have finished.

---

### Post by Rev4n on 2007-09-18
Your post was very detailed and helpful!  Thanks so much for taking the time to help me with this!

---

### Post by jchan2 on 2007-11-14
Hi, I'm really new to using Linux and found this topic similar to my situation. 

I'm currently using Feisty Fawn as a Live cd to rescue files for my friend's Powerbook G4. The Mac OS is corrupted, (I keep getting an error to restart laptop) however I believe the files are still intact. When I used the Live cd, I can see 'Macintosh HD' on the desktop, and I can somewhat browse through the folders but can't access the ones with an 'X,' under 'user' folder because of 'user privileges.' Is there a way to access and backup these files without going through the corrupted Mac OS?

---

### Post by oswaldkelso on 2007-11-15
> **Rev4n said:**
> 

Is there any way for me to access my music files and such that are stored in my User account on the OSX partition?

The way I did this was create a user on my Debian system with the same user name and password as on my osx partition. I can now read all that user data. I can not write to the osx partition.

 I believe that if your osx partition is formatted as hfs you can read and write to it. The standard mac file system is hfs+(plus)  

I have not  set up a hfs partition so I would recommend a little more research.

---

### Post by jchan2 on 2007-11-18
> Hi, I'm really new to using Linux and found this topic similar to my situation.

I'm currently using Feisty Fawn as a Live cd to rescue files for my friend's Powerbook G4. The Mac OS is corrupted, (I keep getting an error to restart laptop) however I believe the files are still intact. When I used the Live cd, I can see 'Macintosh HD' on the desktop, and I can somewhat browse through the folders but can't access the ones with an 'X,' under 'user' folder because of 'user privileges.' Is there a way to access and backup these files without going through the corrupted Mac OS?


Anyone have any idea?

---

### Post by oswaldkelso on 2007-11-18
See my post above: You can try this from the live cd. Create a user with the same user name and password as on the osx machine. login as that user.  Mount an external storage device or cd/dvd burner and copy the files to it.

If you have accsess to another mac with firewire you can clone the data over with ccc 

[http://forums.debian.net/viewtopic.php?t=18193]("http://forums.debian.net/viewtopic.php?t=18193")

In the options you can select which bits you clone over. Obviously you clone to a spare partition or firewire HD (ipod?) dont clone the corrupt mac over the working macs system

---

### Post by frog_pilot on 2007-11-18
you can also start nautilus with root-privileges. Then you can access any file everywhere. simply execute ```
gksu nautilus
```and a nautilus window will open where you have root previliges. but you have to work inside this window. This means you cant drag and drop files out of this window to your desktop, since you are only root inside this window. But you can copy the files inside this window and browse e.g. to the /home/<username>/Desktop folder and paste them there (and anywhere other).

Hope this helps...

---

### Post by jchan2 on 2007-11-20
I used 
```
gksu nautilus
```

However, it only lets me access files on the Linux hard drive, but it doesn't let me access the Mac's. Thanks for your suggestion though, frog_man.

i'll try using your suggestions, oswaldkelso. does this method work pretty well, even with a Live CD?

---

### Post by oswaldkelso on 2007-11-20
I don't know if it works with a live cd. Sorry. If you can see the partitions but not accesses them I think its a permissions thing or that your using the live cd? I don't know tbh.

As I usually use xfce I did this.

From my notes 
note I have two separate osx partitions

This is what i did as root
mkdir /media/emac1
mount /dev/hda9 /media/emac1 -t hfsplus

mkdir /media/emac2
mount /dev/hda10 /media/emac2 -t hfsplus


NOTE:

#emac1 and emac2 are the names of my sparate osx partitions you can call it what you want
#hda9 and hda10 are the partition numbers yours may be a different

#My fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda17      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda19      /home           ext3    defaults        0       2
/dev/hda18      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda9       /media/emac1     hfsplus
/dev/hda10      /media/emac2     hfsplus

Then I made a user with the same name and password as on my osx partition and could accsses the osx partitions but only read not write i.e I can only copy from and not too my osx partitions. As I said before because they are hfs+

EDIT:

Show free disk space

df -h	

Show disks partitions sizes and types (run as root)

fdisk -l

Its a long time since I did this but you could try changing the accesse permissions from osx

From osx command+i on the user then you can change file permissions. Then try accessing from ubuntu

---

### Post by oswaldkelso on 2007-11-21
> **oswaldkelso said:**
> 

Its a long time since I did this but you could try changing the accesse permissions from osx

From osx command+i on the user then you can change file permissions. Then try accessing from ubuntu

Last night I setup my other machine and setup file sharing with osx.

I failed to access with the original owner and password so in osx I setup a new user with administrator privileges and the same user name and password as on my debian install. Then I set ownership and permissions in osx  to the following

ownership and permissions

you can "read & write"

Details

owner "my user name"
access "read & write"

group "my user name"
access "read & write"

others "read only"

Then I was able to access my data on osx but  read only because its hfsplus

Hope that helps

---

### Post by atlfalcons866 on 2007-11-21
do you have hfsutils installed

---

