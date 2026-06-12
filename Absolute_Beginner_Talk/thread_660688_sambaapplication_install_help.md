---
title: "samba/application install help"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-07
Unlike most folks on Absolute Beginner Forum,  I am among the most neophyte, with only 15 years of windows/computer experience!!

Ok, i got ubuntu installed.  Only took me 10 hours and 15 boot disks!  Now, I'd like to install samba, as my primary intention for this first linux install is to be a file server on my network .  I read the sticky guide on installing programs and it looks quite daunting and labor intensive.  I tried thru the applications terminal and nada.

is there a simple step by step, layman's term guide for application installation for those of us with modest experience?  honest truth, i searched to this subject on the forum, and it was well beyond me.  or do you need to have a recent IT degree to use linux (mine is from 1996)!!

Thanks much in advance for the advice!!

---

### Post by lordViN on 2008-01-07
use this guide

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)

search for samba, then follow the guide, the only little consideration to take is that when creating the smbusers file with 
```
gksudo gedit /etc/samba/smbusers
```

you must especify the samba users inside
```
system_username = "network username"

```

this means that in "system_username" you must put the name of the user in linux, and in "network username" you must put the name of the windows user.

---

### Post by juanzo007 on 2008-01-07
Disregard...  figured out how to update my repositories, I think?  Man, either i'm newly dumb, brainwashed by windows, or linux is not intuitive!!

---

### Post by lordViN on 2008-01-07
we all start the same, just remember that patience makes masters. :)

```
sudo apt-get update
```

---

### Post by hyper_ch on 2008-01-07
Well, if you need a very basic samba setup (make linux folders available on Windows) you can use my samba config.

(1) Install samba:
```

sudo apt-get install samba

```

(2) Backup your original samba config file
```

sudo cp /etc/samba/smb.conf smb.conf.org

```

(3) Edit your samba config to something similar:
```

gksudo gedti /etc/samba/smb.conf
[code]
[global]
workgroup = WORKGROUP
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/hyper/Appz

```

Let's get into details:

```

workgroup = WORKGROUP

```
The name of your windows workgroup. If you have not changed it, it should also be "WORKGROUP".

```

hosts deny = 10.0.0.1

```
My router has the IP 10.0.0.1 and I don't want my router (and hence people from outside my lan) access my samba server. Change it to your router's IP address if you also don't want that or cut this line out if you don't care.

```

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

```
This is the folder where Windows users can create AND delete stuff. I created for that an Exchange folder in my home directory and with the force commands I ensure that files will be written to my username and usergroup (which is "hyper").

```

[appz]
comment = Appz
path = /home/hyper/Appz

```
This is a simple read-only examples. Samba users can read from that folder but not modify it.

(4) Add users to samba
Well, with this config you need systemusers on your linux system that can access Samba. The samba users may have different passwords than actualy system users.
To add an existing system user to your samba passwd file you will run this:
```

sudo smbpasswd -a USER

```
And you'll then be prompted twice for the password setup.

(5) Now restart sambe
```

sudo /etc/init.d/samba restart

```

(6) And now you can either browse your network neighbourhood in Windows or use directly the IP of your linux machine to gain access.
Username and password will be according to the added users in step (4).

---

