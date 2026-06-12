---
title: "i cannot modify /etc/sudoers"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-08-27
i,
i'm tring to modify the file sudoers with "sudo gedit /etc/sudoers" to add the string "username ALL= NOPASSWD: /usr/bin/firestarter" but cannot save because gedit says that i'm work with a read-only disk. the permission of /etc/sudoers is 440
thanks

---

### Post by Skia_42 on 2006-08-27
> **ubunlilluz said:**
> i,
i'm tring to modify the file sudoers with "sudo gedit /etc/sudoers" to add the string "username ALL= NOPASSWD: /usr/bin/firestarter" but cannot save because gedit says that i'm work with a read-only disk. the permission of /etc/sudoers is 440
thanks

This command displays all the automatically mounted disks on your computer. Your main drive has a mount point int he root directory "/" could you post the output of:
> cat /etc/fstab

---

### Post by ubunlilluz on 2006-08-28
lillux@lilluxoctavius:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb5       /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdb7       /home     ext3    defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

---

### Post by Fraoch on 2006-08-28
Heh, I'm trying to do exactly the same thing.  I did manage to get this portion working though.

Did you see this *very important* tip in /etc/sudoers?  Near the top.

> # This file MUST be edited with the 'visudo' command as root.

I believe I tried:

```
sudo visudo
```

which edits a sudoers.tmp file.  You then save this file as sudoers without the .tmp and it will tell you you're overwriting.  I said yes.  This may not be the proper way to do it but it works for me and my sudoers file shows the changes.

---

### Post by jb5 on 2007-04-25
Anybody help????

I was trying to edit my sudoers file to get firestarter to load up on login.

However, (a little knowledge is a dangerous thing!) after failing to edit my /etc/sudoers file with the command

sudo gedit /etc/sudoers
I tried to give write permissions to file with the command, from the /etc directory

sudo chmod +w sudoers

and indeed the file now has the following permissions
-rw-r----- 1

After still being unable to edit the file with the command above I tried to set the permissions back to normal with the following command

sudo chmod -w sudoers

but all I get now is the following error when I try any sudo command

sudo: /etc/sudoers is mode 0640 should be 0440

Anybody any ideas how I can get back to the correct permissions?

---

### Post by jb5 on 2007-04-25
Ok.

Managed to find the answer.

Booted into safe mode and from the command line typed

cd /etc
chmod 0440 sudoers
ls -l sudoers      showed the correct permissions
-r--r----- 1 root root ........

Phew, I don't think I could tolerate another install just yet!

---

### Post by bodhi.zazen on 2007-04-25
LOL

You need to edit the file as root. That is why you got the read-only error (when you boot to safe mode you are root :) )

You can use any editor ~
[list=number][*]sudo vim /etc/sudoers[*]sudo nano /etc/sudoers[*]gksudo gedit /etc/sudoers[/list]

BUT YOU SHOULD USE ```
sudo visudo
```

This is because if you make a mistake with /etc/sudoers you may lose root access (well not really because you can always boot to safe mode or use a live CD).

man visudo :> visudo edits the sudoers file in a safe fashion, analogous to vipw(8). visudo locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors. If the sudoers file is currently being edited you will receive a message to try again later.

---

### Post by jb5 on 2007-04-27
Thanks for above.

I was just following the firestarter guide which said "...edit the file with your favourite editor"! LOL

After a bit more digging it would appear that I don't really need to keep running firestarter anyway.

From the info I've found, it would seem that Ubuntu uses iptables to configure the "firewall"; by default the defaults are reasonably secure.
Firestarter is a GUI to facilitate re-configuring the iptables, and once set it should automatically configure the table each time I dial out, (which happens at boot time for me).  

sudo /etc/init.d/firestarter status

Will show if the firestater is running (i.e. has re-configured the tables) or not.

Does this then apply to all users or should I set up firestarter for all accounts? (At the moment I only have one account so not a desperately pressing issue).
The reason I'm unsure is that when restarting after a safe mode boot, one of the lines shows the firestarter session shutting down.

---

### Post by bodhi.zazen on 2007-04-27
> **jb5 said:**
> Thanks for above.

I was just following the firestarter guide which said "...edit the file with your favourite editor"! LOL

You are most welcome :)

> After a bit more digging it would appear that I don't really need to keep running firestarter anyway.

From the info I've found, it would seem that Ubuntu uses iptables to configure the "firewall"; by default the defaults are reasonably secure.
Firestarter is a GUI to facilitate re-configuring the iptables, and once set it should automatically configure the table each time I dial out, (which happens at boot time for me).  

sudo /etc/init.d/firestarter status

Will show if the firestater is running (i.e. has re-configured the tables) or not.

Does this then apply to all users or should I set up firestarter for all accounts? (At the moment I only have one account so not a desperately pressing issue).
The reason I'm unsure is that when restarting after a safe mode boot, one of the lines shows the firestarter session shutting down.

The issue of a firewall is debatable and there are numerous threads in these forums debating exactly this issue.

IMO they can be summarized as follows :

1. For MOST users the default IP tables are secure enough and you do not need to do anything more.

2. If you are not running a server you do not need to add any further firewall protection.

3. For the more let us say paranoid among us you can add a firewall. In that case I would advise you learn iptables : 

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

[http://ubuntuforums.org/showthread.php?&t=159661](http://ubuntuforums.org/showthread.php?&t=159661)

---

