---
title: "Unable to create new user"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-01-31
good evening,
I have been trying to create a new user from the terminal for 2 hours and finally got this: ```
simeon@simeon-laptop:~$ useradd -c Guest -d /home/Guest -p newuser -e 01/04/08 -f 30 -g users -m -s /bin/bash -u 1234 guest
useradd: unable to lock password file
simeon@simeon-laptop:~$ useradd -c Guest -d /home/Guest -e 01/04/08 -f 30 -g users -m -s /bin/bash -u 1234 guest
useradd: unable to lock password file
simeon@simeon-laptop:~$ 
```

What's gone wrong?

---

### Post by jan quark on 2008-01-31
why not using the gui interface?

go to menu > system > administration > users and groups > add new user

---

### Post by LowSky on 2008-01-31
> **jan quark said:**
> why not using the gui interface?

go to menu > system > administration > users and groups > add new user

seems to be the best way to do it

---

### Post by jseiser on 2008-01-31
This is all from the arch linux wiki.  But it should on any linux system.

run this as root. 
useradd -m -s /bin/bash johndoe
 passwd johndoe

The first command will add the user named johndoe to the system, create a home directory for him at /home/johndoe, and place some default login files in his home directory. It will also set his login shell to be /bin/bash. The second command will ask you for a password for the johndoe user. A password is required to activate the account.

to add this user to a certain group

run this as root
usermod -aG [group] [user]

(where [group] is the group you want to add and [user] is the user you want to add to the group) 
This is from arch linux, so discount the arch specific ones, and i would imagine the other group names are common to all linux distros, someone correct me if im wrong.  I got 

Below is a list of common groups and their function in Arch.

    * abs = rights to Arch's build system.
    * audio = sound
    * camera = access to cameras.
    * disk = block devices not affected by other groups such as optical,floppy,storage.
    * floppy = access to floppy drives.
    * kmem = rights to /dev/mem, /dev/port, /dev/kmem
    * log = access to log files in /var/log.
    * lp = printers
    * optical = access to dvd/cd drives.
    * network = right to use Networkmanager (if you want to use NM-Applet or KNetworkmanager you need to be in this group)
    * power = right to suspend etc
    * root = root/admin power (security warning: don't add your user to this unless you know what you're doing!)
    * scanner = scanners
    * slocate = access to command updatedb
    * storage = access to external drives (hard drives, flash/jump drives, mp3 players, etc)
    * thinkpad = for thinkpad users accessing /dev/misc/nvram through e.g. tpb
    * tty = access to serial/USB devices like modems or handhelds
    * users = default users group (recommended)
    * video = DRI/3D acceleration
    * vmware = right to execute vmware
    * wheel = right to use sudo (setup with visudo) (PAM also affects this)

---

### Post by KOTAPAKA on 2008-01-31
I am sorry really I was so stupid I forgot to log in as root ](*,). I just did it :D

---

