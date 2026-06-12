---
title: "My absolute beginner thread."
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by matthx on 2007-12-29
Sup guys, i have installed 7.10 (fist linux experience) and im kinda lost. I think ill figure my way out of my problems but the only one, and yet the most basic one i guess, is that when i try to install something from synaptic (pkg manager) it gives me a warning about me not having administrative privileges. So now i want to edit or even check out my user privileges. 

When i right click on the user switcher icon in the main panel, i click on "Edit users and groups" and then it asks me for a password. I tough it was the same password i used for my user (matth) when i installed Ubuntu so i typed it in but it gave me a bad password warning and closed... I retried but it never worked. I tried to leave it blank and when i hit enter it gives me no bad pass warning and it closes the window just like it was the good password but nothing else happens.

My question[SIZE="1"](s)[/SIZE] is[SIZE="1"](are)[/SIZE]: do i have to log in as an admin/root/super user on the login screen when Ubuntu boots up to have administrator like privileges? And if i do what are default user/pw for this because other than my own user/pw i have not entered any other password during installation. Or even can i simply have admin like privileges when im logged in as my own user (in this case matth). Is there an other way to check out or change out user privileges? I searched the system menu from the main panel and i got nothing. Its kinda frustrating to get asked for a password every time i want to do something on my own computer and nothing works...

Thanks in advance. :KS

---

### Post by pavel989 on 2007-12-29
this is odd, you shouldn't ahve to log in with root. but your password should give you  "super" privledges. 
super reffering to the root account, if you will.

But the reason it does this is so that it can keep at least some level of security. its a bad idea to log in with root because sometiems you might accidentally break your system. And the only time it really asks for you password is when you are dealing with root folders, which means installs, and some file editing.

For that matter, how did you log in? it should be the same password

---

### Post by matthx on 2007-12-29
Here is an example of what i want to do... I want to launch the users-admin application to check out and change my privileges because when i want to install packages with synaptic it tells me that i dont have the appropriate privileges to install them. So when i launch the users-admin application it asks me for a password. I type in the only password i entered during installation (and its the one for my user account when i start Ubuntu) but it doesnt work. It gives me this exact error.

"Failed to run users-admin as user root. The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

And for your question: I remember trying to run synaptic and input my password to run users-admin program right after a reboot.

---

### Post by jas0 on 2007-12-29
matthx, you are already an administrator. If you are familiar with Vista, you will recognize how the process works, sort of. Instead clicking "yes" on the "are you sure you want to do this" dialog box, you need to tell it that you are indeed sure you want to do what you want to do--proactively.

First of all, if you're using the GUI Synaptic package manager, you ought to be asked for your password right after clicking the icon.

If you really want to run the users-admin app, just open up Terminal and type
```
sudo users-admin
input your password
```

If you want to get a root Terminal window, just enter
```
sudo -s
```

Everything you enter after sudo -s will be run as a privileged user without the sudo part.

---

### Post by r4ik on 2007-12-29
Try,

Ctrl-Alt-F1 (get's you in the command line)

sudo adduser username admin (where username is you're username)

That one command will add user username to the admin group so you can sudo 

Ctrl-Alt-F7 get's you back in the GUI again.

Good luck !

---

### Post by ugm6hr on 2007-12-29
This might help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Although if you have just installed, with yourself as the only user, then I can't work out why you can't install anything.  Are you the only user?  Does Synaptic even ask for your password when you try and install?

---

### Post by matthx on 2007-12-29
Synaptic doesn't even asks me for a password. It just warns me that i wont be able to install packages because i don't have the proper privileges. And every time i input a password in the GUI or a terminal window (except when i log in to Ubuntu) it either doesnt do anything or tells me its a bad password and i only have one... Ill try more today but if i cant get it to work ill reinstall with the hopes it changes something. I really wan't to learn about Linux but i feel that im limited from everywhere as if i was on a high school computer...

---

### Post by ugm6hr on 2007-12-29
> **matthx said:**
> Synaptic doesn't even asks me for a password. It just warns me that i wont be able to install packages because i don't have the proper privileges. And every time i input a password in the GUI or a terminal window (except when i log in to Ubuntu) it either doesnt do anything or tells me its a bad password and i only have one... Ill try more today but if i cant get it to work ill reinstall with the hopes it changes something. I really wan't to learn about Linux but i feel that im limited from everywhere as if i was on a high school computer...

If you haven't done anything - then it will probably be easiest just to delete the partition and re-install.

Make sure you only create a single user when you install - that way it will always be the administrator.

---

### Post by matthx on 2007-12-29
Ok i just reinstalled Ubuntu. It fixed it. I can now access things i could not get before. Thanks guys. Now lets learn how this thing works!

---

