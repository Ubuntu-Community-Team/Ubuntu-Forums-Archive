---
title: "user login &quot;Permission Denied&quot;"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by anuragp12@gmail.com on 2008-01-28
Hi Everyone
I am a newbie to Linux and this is my first post to the forum. 
I am trying to install samba as the PDC for my company. I was configuring LDAP and did a reboot.I have since not been able to logon using my username. The error message i get is "Permission Denied". I can however logon using Webmin. and also login to samba from a windows machine. 
Can someone please tell me how to again enable my user account. 
Thanks
Anurag

---

### Post by jw5801 on 2008-01-28
Is there any more information or just "Permission Denied"? Try pressing ctrl+alt+F6 after reaching the login screen, and login via the shell rather than through GDM (the Gnome graphical login manager), that might give us more information. If you can get to a command line as another user try running ```
ls -la /home/
``` and check that you own your home directory. If for some reason the permissions or ownership of the user home directory has changed, the user will be locked out of their account.

---

### Post by anuragp12@gmail.com on 2008-01-29
I do not have any other login  but i can go to the recovery console and login as root. When I login through the GUI i get the message "Authentication Failure". When I login in through CLI, I get the usual message about warranty of Ubuntu (the same one when u have a successful login) and then the message says "Permission Denied" and logs me out. 

I checked, I am the owner of my home directory.  Can I make another user and work through it for the time being, till this gets resolved? Given that I have root access, I can execute any command. 

Thanks
Anurag

---

### Post by jw5801 on 2008-01-29
Yeah, that should work. I'm not sure the exact options and all that you'd need to enter, but the command that adds new users is simply "adduser" ```
man adduser
``` will give you alot more information.

---

