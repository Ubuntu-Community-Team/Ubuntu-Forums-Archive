---
title: "sharing folders"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by jshamash66 on 2006-10-03
I'm a linux newbie (been running Ubuntu for about 2 hours now) and I'm having trouble sharing folders with computers running XP on my network. I installed Samba, and set up a folder to be shared (via right-click), but my XP computers won't find my Ubuntu one, and vice versa. All the websites I've found that deal with this subject are too complicated for me (I have absolutely no experience with Terminal, or anything like that) so any help using VERY basic terms will be much appreciated. Thanks!

---

### Post by bodhi.zazen on 2006-10-03
Try this:

[Easy File Share](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by jshamash66 on 2006-10-03
> **bodhi.zazen said:**
> Try this:

[Easy File Share](http://ubuntuforums.org/showthread.php?t=218630)

Nah, FTP won't do the job. I need to set up a shared folder so that I can transfer my BitTorrent downloads from one pc to another, and FTP would be too slow for that. But thanks anyway, and maybe I'll try it out just to see how it goes.

---

### Post by hyper_ch on 2006-10-03
Here's my samba config:

```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2006/09/29 19:14:58

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1, 10.0.0.2

[exchange]
comment = Exchange
path = /home/exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/samba

```

Just adjust the settings to your need and add the usres that shall have access also to samba...
It works for me so far.
10.0.0.1 = Router
10.0.0.2 = Wifi Access Point

---

### Post by jshamash66 on 2006-10-03
Sorry I'm such a newbie, but I still don't know what to do. How do I access the samba config file? And what users do I want to have access to Samba? The users on my Ubuntu computer?

---

### Post by hyper_ch on 2006-10-03
> **jshamash66 said:**
> Sorry I'm such a newbie, but I still don't know what to do. How do I access the samba config file? And what users do I want to have access to Samba? The users on my Ubuntu computer?

Well, first you need to install samba:

1.) Open a terminal
2.) Type
```

sudo apt-get install samba

```

After that you need to adjust the samba setting

1.) Make a copy of the default config --> In the terminal type:
```

sudo mv /etc/samba/smb.conf /etc/smb/smb.conf.org

```
2.) Then you need need to create you new config file --> in the terminal type:
```

sudo nano /etc/samba/smb.conf

```

And paste this code below... however adjust the settings that you need:

```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2006/09/29 19:14:58

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1, 10.0.0.2

[exchange]
comment = Exchange
path = /home/exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/samba

```

workgroup --> The name of the windows workgroup you are in. In German the default is "ARBEITSGRUPPE" in english the default is "WORKGROUP". If you don't know yours, google for it (keys something like "how to change workgroup in windows"....)
hosts deny --> Enter IP addresses in there that shall have no access to the machine. I added the wifi access point and router to my config as I don't want to have connections from outside...

For the exchange share (where everybody in the lan can write to) I have set force user and force group to my own user that so that "I" can easily access and move things there... :)
path --> This is where the share is located on the samba machine
read only = no --> so people can write...

For the appz folder (where I have some windows appz, movies, mp3s.... there is only read-only. Peopl can access it and download but cannot share...

3.) Well, once you pasted in what you need press   ctrl-x   for exiting nano and then "y" to save the document.

4.) After that, you need to reload samba --> in the terminal type:
```

sudo /etc/init.d/samba restart

```

Now you need to add users that can actually connect to it (this is a bit tricky I think and I don't know if you can get it to work without system users...)

1.) For each different user in the network that shall have access you need to create a system user (however you can create like 1 "shared" user through all windows computers connect --> In the terminal type the following to create a new user:
```

sudo useradd USER

```
Replace USER with the actual username that you desire can login and be careful about the spelling (case sensitivity on linux)

2.) Make a password for the user --> in the terminal type the following:
```

sudo passwd USER

```
You'll be prompted twice for the password.

3.) Then you have to add the userpasswd to the samba config --> in the terminal type this:
```

sudo smbpasswd –a USER

```

After that in windows in the network environment (Windows Networks) you should see your linux computer and when you want to access it you will be prompted for a username and passwd.
You then type the details with which you created the new user.

---

### Post by warjowuch on 2006-10-03
Hi there, thanks for your howto. I have set it up a few days ago, following another one (with exactly same things).

I only have one problem: the windows XP computer can acces my ubuntu-one, but I cannot find the windows XP shares. (they're just right-clicked folders: share)

Do you know the problem?

---

### Post by hyper_ch on 2006-10-03
Hmmm, I don't know about accessing windows xp shares... sorry :(

---

### Post by warjowuch on 2006-10-03
I replace myself/my part of this discussion to this thread:

[http://ubuntuforums.org/showthread.php?p=1574976#post1574976](http://ubuntuforums.org/showthread.php?p=1574976#post1574976)

---

### Post by jshamash66 on 2006-10-03
Thanks alot for the howto. My only question is about the adding users part- is the user just the username that other computers will have to use in order to access my Ubuntu computer? Or do I have to set up multiple usernames for the various computers on my network? For now, I added the user "HP2005", which is the name of the windows computer that I want to be able to access my Ubuntu shared folders. However, HP2005 still can't find my linux computer (I'm sure I have the right workgroup, and everything)! Do you know what the problem is?

---

### Post by hyper_ch on 2006-10-03
The username you create on your ubuntu machine creates a "usser account" on your ubuntu machine.

All the windows machines can then use HP2005 + the password to get access to the samba share.

If you know you ubuntu box name you can manually add the network share to the windows machines.
go to the network place (don't know what that is exactely called in English) and add a manual share.

Use then:

```

\\LINUX_NAME\SHARE

```

You have to replace LINUX_NAME with the name of your ubuntu box and SHARE with the directory description (in my cases above it will be either "appz" or "exchange"

---

