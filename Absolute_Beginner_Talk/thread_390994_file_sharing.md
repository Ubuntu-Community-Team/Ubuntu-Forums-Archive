---
title: "file sharing"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by FITorion on 2007-03-22
maybe someone here will know...

I want to turn on file sharing...

I want to have many users who are running windows and accessed the computer by searching for its name

they can only see and access the "Shared" file

they can download from any file in the "shared" file and only upload to the "upload" file in the "shared" file

How?

---

### Post by mrmonday on 2007-03-22
If you right click a file, you can set it to shared, and choose permissions.

---

### Post by FITorion on 2007-03-22
I've tried that...

there isn't anywhere where you can set permissions for specific users

there isn't anywhere to set up users



and while I can see the computer from another computer I can't access the shared file

and if I move that computer to some where a little further away on the network... I can't see it at all

---

### Post by FITorion on 2007-03-22
i found this 

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing)


now I need to know how to find my IP

---

### Post by OMRebel on 2007-03-22
Drop to a terminal window and type in:
ip addr

That'll give you your IP address.

---

### Post by AndyCooll on 2007-03-22
For Windoze to see file shares you need Samba installed and then use the file sharing facility (Administration > Shared Folders)

:cool:

---

### Post by Matthamilton23 on 2007-03-25
um windows prompts me for a password when I try to connect to my xubuntu drake machine. what password is this???

I have tryed my default username and password but to no effect 

Can somebody help me???

---

### Post by FITorion on 2007-03-25
you need to set up a samba user account 

sudo smbpasswd -L -a your_usermane

it'll prompt for pass word
enter the same info you use to login to your machine

sudo smbpasswd -L -e your_username

that enables the account.


that should help you Matthamilton23

---

### Post by cowlip on 2007-03-25
You need to a Samba user with smbpassword -a .  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


Comment on this bug to show developers that it's a problem: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

---

### Post by FITorion on 2007-04-06
one more question ...

Now that I got this all working... I'd like to set up a log file of some sort.  I want to log who logs in and what they download and upload.  how do I do that?

---

