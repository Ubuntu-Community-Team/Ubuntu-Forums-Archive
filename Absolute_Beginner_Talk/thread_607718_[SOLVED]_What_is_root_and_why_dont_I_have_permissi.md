---
title: "[SOLVED] What is root and why dont I have permission??"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bluespider on 2007-11-09
In trying to enable read write permission on the 1394a folder in my  dev and I cant do it,I keep gettng this message that only root can do it, what is  root and why dont I have permission to do anything I want on my own computer?? Ubuntu is starting to seem a lot like Vista ! While Im at it what are emblems ?? What do they do ??

---

### Post by Steve1961 on 2007-11-09
The root account is not something you should use in Linux as you can cause serious damage to your system if you don't know what your doing.  To gain temporary root privileges preface any command with the word sudo.  Here's a link:

[http://www.linuxdevcenter.com/pub/a/linux/2005/12/01/linux_root.html](http://www.linuxdevcenter.com/pub/a/linux/2005/12/01/linux_root.html)

---

### Post by hyper_ch on 2007-11-09
Au contraire, Linux is quite different from Vista... you see, linux is setup for multi-users so normally you do not need to mess around with permissions... and if you do, you better know what you're doing.

Root is the system administrator... the almight account on a linux computer and on ubuntu it's deactivated by default. Instead of acquiring root user you should use "sudo" instead. Check the ubuntu wiki what sudo is and how to use it.

---

### Post by kellemes on 2007-11-09
> **bluespider said:**
> In trying to enable read write permission on the 1394a folder in my  dev and I cant do it,I keep gettng this message that only root can do it, what is  root and why dont I have permission to do anything I want on my own computer?? Ubuntu is starting to seem a lot like Vista !

First investigate..
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29")

And please don't try to make comparisons with other products simply because you have a problem you haven't investigated, it's pointless and in general not appreciated.

---

### Post by Shinbu-Otaku on 2007-11-09
1) ubuntu is nothing like vista, ubuntu ACTUALLY works lol

2) Root is the 'super-user' and has access to everything and anything. When you install ubuntu it asks you to input a root password. Whenever a password box comes up (other than to log in) you will need to use the root password. Not 100% sure, but when you go to the terminal and type 'sudo' (without the speech marks) and push enter, then put in the root password as it asks, you get super-user rights, meaning you can do what you need. This should solve your problem.

---

### Post by afeasfaerw23231233 on 2007-11-09
it is for safety reason. root is the only user who has the whole power on your system. actually you are root but you usually log in your system as another user, says 'user1'. when you have to do some administrative work, it will ask you for a password for root. that password was set when you install ubuntu. after you type in that password you will act as root temporarily.

---

### Post by Marc Hoffman on 2007-11-09
To add my 10p's worth- not having root permissions as standard is part of the security model that helps prevent Ubuntu/Linux from becoming like Windows in that viruses and unwanted scripts aren't able to run in the first place.

---

### Post by bluespider on 2007-11-09
So if Put sudo into the terminal window I will then be able to go to the 1394a folder and enable read and write for  my 1394a firewire port ??

---

### Post by philinux on 2007-11-09
I'd use in the terminal 
```
gksudo nautilus
```
 and then browse to your file and do what you will.

Just be careful and sure you know what your doing that's all.

---

### Post by bluespider on 2007-11-09
Thank you phillinux That did the job, now my firewire is working, Much appreciated.

---

### Post by aonegodman on 2007-12-13
When I just installed Ubuntu it asked me for my "real name", "user name", "password x2".

It did not ask me to choose or offer to change administrator or root password.

But there is one and my quest this morning is to find it. Can you help me?

What is default if any?

Thanks!

---

### Post by Anicka on 2007-12-13
You as the first user will have super-user permissions, that is when you need extra powers, you type sudo in front of the command (sudo apt-get update). You will be prompted for a password, but it is your own password that you have to type. For any new users that you create, you can choose if they should or should not have admin-permissions or not.

---

