---
title: "the difference between network feature in ubuntu and fedora"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dtzxdtzx on 2007-04-21
Hi,

Since I have network issue and it works in fedora but not in ubuntu, Could anyone tell me what network feature is missing comparing with fedora?

thanks

Frank

---

### Post by BoneKracker on 2007-04-21
I think you will do better if you can provide some information regarding your problem.  Fundamentally, they have the same networking capabilities.

What do you get when you type the command  sudo ifconfig

---

### Post by dtzxdtzx on 2007-04-22
I have posted a couple of message for the same problem and did not receive any solution. That is why I asked this general question. My problem is


I installed the 7.0.4 and tried the following command:

sudo mount -t cifs -o username="domain/frank" -o uid="500" //198.162.1.1/hostC ~frank/hostC

I typed my password and got the response "Sorry, try again". After three times, it says "sudo: 3 incorrect pasword attempts"

I can ping the id 198.162.1.1. The mount command works in fedora also. Can someoen help me to figure out why? 

Thanks

Frank

---

### Post by BoneKracker on 2007-04-22
The error message you are getting is from the authentication system (PAM) on your system.  It's not a newtorking issue, it's an authentication issue.  

It's telling you that user/password combination is either incorrect or not authorized to sudo.

Are you using the correct username and uid?

Does samba/cifs otherwise work for you?  I.e., can you open the graphical tool and browse to that host?  Can you log in using the graphical tool  (on the menu, Places, Network, Windows Network, <host>) or the connect to tool (Places, Connect to Server, Windows Share, etc.)?

However, another possibility (also not a networking issue, but a filesystem issue), is that you are trying to mount a newtork filesystem.  I assume that mounting a cifs partition is enabled in the kernel or a module, but it's possible that it's not.

---

### Post by dtzxdtzx on 2007-04-23
Thanks for trying to help me.

I can open the shared folder on other machine by using graphical tools, the login works fine. However, the mount command as before does not work. Then instead of directly using sudo command, I first use sudo -i to get into the su mode, then I type the same command with sudo in front of it. Here is the message I got:

mount: block device ipaddress/hostC is write-protected, mounting read-only
mount: cannot mount block device ipaddress/hostC read-only.

It seems that I cound not mount the drive. I have similar problem with previouse version of ubuntu.

Thanks

Frank

---

