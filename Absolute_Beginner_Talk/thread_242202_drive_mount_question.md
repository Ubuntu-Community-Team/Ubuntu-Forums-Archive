---
title: "drive mount question"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by vincent orange on 2006-08-23
Hello,

I'm about to edit my /etc/fstab file to mount 3 more hd's. My question is that does it matter what the mount point is? I'm asking as all the drives are the same size but were mounted in another system like

/kangaroo
/lion
/snake


When mounting them in the new system do I have to use the same mount point, or use anything I lke?

Thanks
VO

---

### Post by bulldog on 2006-08-23
You can make three folders in /mnt and call them what you like.

You must use the /mnt folder.

---

### Post by kinematic on 2006-08-23
> **bulldog said:**
> You can make three folders in /mnt and call them what you like.

You must use the /mnt folder.


no you don't.
you could also mount a drive in your /home directory....../home/vincent orange/hda# for example.
or you could make a new directory in your root tree and call it /data and mount a drive as /data/hda#.
your not confined to /mnt.

---

### Post by vincent orange on 2006-08-23
so it doesn't matter what the mount point for the drives are even if they were named something else on a past system?

thanks for your replies

---

### Post by kinematic on 2006-08-23
no,it doesn't matter what they were called on a past system.
a few weeks ago i was explaining how mounting works to a friend and created a directory in /home/kinematic/.kde and called it data.
i then used /home/kinematic/.kde/data as mountpoint in fstab and remounted the drive on the fly and he could access it.
a mountpoint is just a directory where the system accesses your drive but for the sake of simplicity i would just use /mnt or /media as those are already there.
and your also not limited by the number of three.....i added two new drives 2 weeks ago both with 3 partitions each next to the drive i already had that has 2 partitions and have access to all 8 of them.

---

### Post by vincent orange on 2006-08-23
> **kinematic said:**
> no,it doesn't matter what they were called on a past system.
a few weeks ago i was explaining how mounting works to a friend and created a directory in /home/kinematic/.kde and called it data.
i then used /home/kinematic/.kde/data as mountpoint in fstab and remounted the drive on the fly and he could access it.
a mountpoint is just a directory where the system accesses your drive but for the sake of simplicity i would just use /mnt or /media as those are already there.
and your also not limited by the number of three.....i added two new drives 2 weeks ago both with 3 partitions each next to the drive i already had that has 2 partitions and have access to all 8 of them.

very helpful, thank you very much for the advice, thankyou

---

### Post by frafu on 2006-08-23
Hello, 

Could you please tell me under what condition a mounted partition or folder appears as an Icon when selecting "Computer" in Nautilius? 

frafu

---

### Post by vincent orange on 2006-08-24
I need some assistance with the fstab file. I tried but it' not mouting the drives on boot.

Here is the file before I added the lines
> 
  GNU nano 1.3.10                           File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 1    1
/dev/hda5       none            swap    sw              0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Now one of the drives I want to add is a SATA drive. Do I add it like this?

> /dev/sda        /media/sda      ext3    defaults       0         0


some input would be really handy, I apprecaite the help already.

---

### Post by bodhi.zazen on 2006-08-24
Change
```
/dev/sda /media/sda ext3 defaults 0 0
```

to
```
/dev/sda1 /media/sda ext3 auto,user,rw 0 0
```

The "default" does not mount on boot -> change to auto.
rw allows read write access.
user allows users (and not only root) to mount/umount.

---

### Post by vincent orange on 2006-08-24
thanks for a fast reply, i  really appreaciet it. I tried what you have suggested but I get the following system response.

> Could not mount device.
The reported error was:
mount: mount point /media/sda does not exist

here is my fstab file

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 1    1
/dev/hda5       none            swap    sw              0       2

# user data drives
/dev/hdb1       /media/hdb      ext3    auto,user,rw    0       0
/dev/sda1       /media/sda      ext3    auto,user,rw    0       0
/dev/sdb1       /media/sdb      ext3    auto,user,rw    0       0

#removable media
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by kinematic on 2006-08-24
did you create the /media/sda directory?
if not do this:sudo mkdir /media/sda(mkdir stands for make directory)
that will create a sda folder under /media wich the system uses to mount the drive at.(btw...you can also add exec or noexec to fstab wich allows or denies you to execute binaries on the partition).

edit:i'll also give you what you need to set the permissions to use the partition as user in advance ;) 
first do:sudo chown -R username:username /dev/sda1(changes the permissions recursively for everything on the partition to your user account).
next do sudo chmod -R 755 /dev/sda1(recursively makes it world read/writeable).

---

### Post by bodhi.zazen on 2006-08-24
Do as kinematic advised except rather then

```
sudo chmod -R 755 /dev/sda1
```

use
```
sudo chmod 755 /media/sda
```

you may also want to
```
sudo chown root:user /media/sda
```

---

### Post by Drakkor on 2006-08-24
Hmmmmm........, kinematic
I'm also trying to mount a partition that was a windows ntfs partition,but I formatted it and changed it to ext3 last night,now I want to change it's name and mount it from windows3 to another folder name,but got this !
Thanks ! :) 

drakkor@drakkor:~$ sudo mkdir
mkdir: missing operand
Try `mkdir --help' for more information.
drakkor@drakkor:~$ mkdir --help
Usage: mkdir [OPTION] DIRECTORY...
Create the DIRECTORY(ies), if they do not already exist.

  -Z, --context=CONTEXT (SELinux) set security context to CONTEXT
Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set permission mode (as in chmod), not rwxrwxrwx - umask
  -p, --parents     no error if existing, make parent directories as needed
  -v, --verbose     print a message for each created directory
      --help     display this help and exit
      --version  output version information and exit

Report bugs to <bug-coreutils@gnu.org>.
drakkor@drakkor:~$

---

### Post by kinematic on 2006-08-24
doh!...you're right about /media/sda :( 
and the -R option is a bit premature now that i think about it...there's nothing on it yet so there's nothing to change recursively :redface:

---

### Post by kinematic on 2006-08-24
@ drakkor

you have to specify the directory you want to create as in sudo mkdir /media/hda# or /media/sda#.

---

### Post by aysiu on 2006-08-24
Actually, the default *does* mount on boot.

Read this:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by kinematic on 2006-08-24
> **bodhi.zazen said:**
> you may also want to
```
sudo chown root:user /media/sda
```

if he wants to be the owner he has to change root to his username.
sudo chown vincent orange:vincent orange makes him the owner and makes it a part of the vincent orange group

---

### Post by Drakkor on 2006-08-24
Thanks, kinematic , I was able to make a directory,"Foghorn",lol,one of my favorite cartoon characters,lol :p  I have done it before but I guess I forgot !  I was wondering if my fstab,as far as options and permissions look OK ? Thanks ! :D  Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto,exec    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /Foghorn        ext3    rw,user,auto,exec    0       0

---

### Post by bodhi.zazen on 2006-08-24
> **kinematic said:**
> if he wants to be the owner he has to change root to his username.
sudo chown vincent orange:vincent orange makes him the owner and makes it a part of the vincent orange group

Thanks. Either works, for some reason I feel better if my disks are owned by root and manage user privileges via group management. Easier if a multi-user environment.

For a personal drive I use root:user_name.

---

### Post by kinematic on 2006-08-24
for /dev/hda6 you have read/write,user can mount/unmount,it's mounted on boot and you can execute binaries on it.
if that's what you want you're ok ;)

---

### Post by kinematic on 2006-08-24
> **bodhi.zazen said:**
> Thanks. Either works, for some reason I feel better if my disks are owned by root and manage user privileges via group management. Easier if a multi-user environment.

For a personal drive I use root:user_name.

hadn't thought about it like that.
me and my wife have one user account for the both of us and we only have music/movies and photo's on our storage partition so we made ourselves the owner.
but i guess your way is safer ;)

---

### Post by vincent orange on 2006-08-25
thanks kinematic, I followed your advice and the drives are mounted now. I didn't use the -R function as you pointed out in your earlier post.

Much respect to the ubuntu forum users

peace
vincent

---

### Post by vincent orange on 2006-08-25
> **aysiu said:**
> Actually, the default *does* mount on boot.

Read this:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

I read this very same page when I was trying to mount the drives, I used default but never worked on my system. I'm not experienced enough to know why though.

---

### Post by kinematic on 2006-08-25
> **vincent orange said:**
> thanks kinematic, I followed your advice and the drives are mounted now. I didn't use the -R function as you pointed out in your earlier post.

Much respect to the ubuntu forum users

peace
vincent

cool...glad you got it to work :D 
and it's kinda cool that i'm now able to help people.
my girlfriend and i started to use linux in november 2005 and it's incredible how much we've learned about computers since then.
it's nice to know we're not n00bs anymore and are advancing to the point were we can help others(we currently dualboot with fedora core and she's a regular over there).

---

