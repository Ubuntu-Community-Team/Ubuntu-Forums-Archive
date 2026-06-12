---
title: "ubuntu + webmin to replace windows xp as &quot;file server&quot;"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ZenMasta on 2007-09-05
Hi,
I need some help setting up ubuntu as a file server on a windows network.

I already have installed ubuntu, webmin and samba is installed too.  I can see the server on all of the windows computers. Now I just need help setting up the sharing directories, user accounts and permissions etc. But I have some questions first.

Should I create a folder in an existing users home directory or somewhere else (does it matter?)? 
Will each client need a username and password to access the files and will they need it for each time the access a file or only the first time they try to access until they reboot?
Is it possible to share without requiring a username/password? Our win xp computers don't ask for passwords when sharing folders, only our old nt 4.0 server(I know, totally old eh? hehe). 

I had tried following some steps on the suggested similar threads but I got stopped when it came to editing the smb.conf file. I think the problem is that I don't have any mime types associated with any programs so that's my guess why it doesn't work. But also most of the threads (I think all) had some gui instructions too that I can't follow since I'm using webmin and console only.

> sudo nano -w /etc/samba/smb.conf
Error opening terminal: unknown.

Additionally, I've tried using the File Manager in webmin to try and create a folder and share using the sharing button but when I try to access from other pcs I'm prompted for a username and password. I've tried a username/password of one of the users on ubuntu but it keeps asking for a un/pass.

Thanks.

---

### Post by dsauxier on 2007-09-06
Take a look in /etc/samba/smb.conf 
There are named sections with specific configurations.
See what the "guest ok" and "guest only" parameters are set to.
Examples ...
This one does not require a password (if that's what you want, then you don't need to read any further) : 
[pub]
        path = /mnt/data/shared
        read only = no
        guest ok = yes
        guest only = yes
        follow symlinks = yes

These do require a password
[homes]
   comment = Home Directories
   browseable = no
   create mode = 0600
   directory mode = 0700
   path = %H
   read only = no
   valid users = %S
[data]
        path = /mnt/data
        read only = no
        guest ok = no
        guest only = no
        create mask = 0770
        directory mask = 0770

If you are using a password, then you must create a unix account/group for the machine and the user.  I don't pretend to remember all of the details, but I've extracted some commands from a couple of shell scripts that I created when I was researching it.

Before users can authenticate you have to set the root samba password
(remember this because you will need to use it to authenticate each user/machine the first time)
smbpasswd -a root

#This adds the linux user and group
useradd -g yourgroupname -d /mnt/home/yourusername -m -p change yourusername
# this adds the samba user
smbpasswd -a yourusername

# replace "machine_name" with the actual machine name
MACHINE="machine_name\$"
echo "Adding group $MACHINE"
addgroup machine_name
echo "Adding Linux user $MACHINE"
useradd -g machine_name -p machinepwd $MACHINE
echo "Adding Samba machine user machine_name"
smbpasswd -a -m machine_name

On Windows XP, you have to sign in the first time using the root samba password

I found this documentation very helpful : [http://www.math.temple.edu/computing/samba.html](http://www.math.temple.edu/computing/samba.html)

---

### Post by ZenMasta on 2007-09-06
I'd be happy to try that, but you missed the bottom part of my post because I can't open the conf.

---

### Post by reckless2k2 on 2007-09-06
i know this may be out there but you might want to try something much more simple like freenas as your solution.

---

### Post by dsauxier on 2007-09-06
Sorry about that...

First, open a terminal 
[INDENT]Applications -> Accessories -> Terminal[/INDENT]

Then (in the terminal) type in 
[INDENT]sudo gvim /etc/samba/smb.conf[/INDENT]
(sudo will prompt for your password)

---

