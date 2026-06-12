---
title: "Passw'd problem on LAN"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2006-12-28
I have installed ubuntu 6.10 and have a LAN with 2 XP computers.
I can access the XP boxes from the ubuntu computer(everything works fine), however when I try to access the ubuntu comp. from XP I get a login box asking for a user name and password.
This is not the same user name and password that I log in with to start ubuntu.
Can someone tell me or point me to some step by step solution?
I am the only one on this LAN so it would be great if I could just eliminate this logon step if possible.
This is my first exposure to Linux so I am just about clueless.
Thanks for any help.
Milt

---

### Post by jonathan.lees on 2006-12-28
What are you using to connect to the Ubuntu box from XP? For example is it SSH or VNC or Samba etc

---

### Post by Milt888 on 2006-12-28
It must be Samba. It seemed to install the LAN on it's own. I may have answered some questions, but I don't remember. (really clueless)
When I open the "workgroup computers/Mshome" window, the " milton-desktop server(Samba,Ubuntu) ( Milton-desktop) text appears below the icon for the Ubuntu box.

---

### Post by jonathan.lees on 2006-12-28
You probably need to do a bit more configuring on Samba to get it working properly. Here's a [link]("http://www.ubuntuforums.org/showthread.php?t=202605") to a HOWTO thread on this forum.

---

### Post by Milt888 on 2006-12-28
Many thanks for the link.
I'll see if I can stumble through those things.
I thought that if I could open Samba, I might be able to make some changes there, but I don't know how to even find the prog.

---

### Post by echo $USER on 2006-12-28
You need to set the samba password on the ubuntu box.  Something like...

> sudo smbpasswd -a system_username

---

### Post by Milt888 on 2006-12-28
Thanks for the advice, but how do I do that?
Do I just copy and paste your quote into the terminal window?
Sorry to ask these dumb questions but...

---

### Post by echo $USER on 2006-12-28
> **Milt888 said:**
> Thanks for the advice, but how do I do that?
Do I just copy and paste your quote into the terminal window?
Sorry to ask these dumb questions but...

Let say I want my user name for samba to be dboyd...

open termianl and I would type...

 sudo smbpasswd -a dboyd

then it asks to type a password, dont worry if nothing is echoed when you type in your password it is for security reasons.  then it asks to type in again.

after that, restart samba...

sudo /etc/init.d/sambd restart

then you can log in from another machine in your workgroup using the username and passwd you just created.


More examples here...

[http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

---

### Post by Milt888 on 2006-12-29
Well, thanks to you guys I managed to get past the "username-password" problem, but when I access the ubuntu box from the XP computers, I click on the icon and get a "printers-faxes" icon instead of the files on the computer. I thought I configured the folder sharing option correctly, but who knows? 
Anyway, thanks for your help.
Milt

---

### Post by Milt888 on 2006-12-29
OK guys; I finally got the thing figured out.
The folder sharing was not configured correctly and the XP firewalls must have had access blocked from the ubuntu box.
Anyway I couldn't have done it without your help.
Many thanks--Milt

---

### Post by echo $USER on 2006-12-29
Anytime

---

### Post by Milt888 on 2006-12-29
Hey if I had seen that alafreakinbama sooner I might have loaded this thing up and brought it down; if you're not too far south (or an Auburn fan).
I'm in chattadamnnooga.
Got the dadgum printer going on my own...
Maybe your info. will save someone else some misery.
Milt

---

