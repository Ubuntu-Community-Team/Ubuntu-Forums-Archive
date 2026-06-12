---
title: "A couple questions..."
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Brian L on 2006-10-08
I'm having trouble with my Ubuntu 6.06 server (default LAMP).

The first one is with permissions. Since I'm a windows user, I'm pretty much used to being able to edit anything I want. Unfortunatly, the user system in Ubuntu confuses me. I'm trying to create a configuration file for my Eggdrop IRC bot by typing in "./configure" but Ubuntu is telling me that I don't have permission to do that. I don't understand this. Does it have to do with sudo or something like that? I don't understand that either really.

My other question is about Apache 2.0. I've been trying to change the default directory for it from /var/www/ to /home/admin/www/ for convienece's sake, and can't seem to figure it out.

Can nayone help me with either of my questions. It's been a long night :(.](*,)

---

### Post by dmizer on 2006-10-08
you'll probably not like this at first, but your not being able to edit whatever you want is actually a feature rather than a problem.

one of the primary reasons windows has problems with getting virus and spyware infections is because users are created as administrators by default, meaning that anyone who can gain access to the computer can make critical file and system changes.

all you need to do in order to get things done the way you want is to prefix the command with "sudo"  this will assign temporary administrator rights while remaining in the safety of a non administrator account.

so to apply this to your situation:
```
sudo ./configure
```
this will accomplish what you need.

about /var/www ... this directory does not have user write privelages.  this may seem like a real pain at first, but really, this is much safer, and will make it much more difficult for someone to hack your website.

---

### Post by 3rdalbum on 2006-10-08
It's all to do with a little thing called the "execute permission". Linux doesn't allow you to run a program unless that program has been marked as "okay to run".

```
chmod +x configure
```

This **ch**anges the **mod**e of the file named *configure*, by adding (+) the executable permission (x). For all the information you'll ever need on changing permissions, type man chmod at the command-line.

Sudo is another difficult thing for users of a non-Unix-like operating system to initially grasp, but it's quite simple really. The account that you have with the system is only a limited account - as you observed, you can't just edit anything you want immediately. You can't run certain programs or access certain services. This is to guarantee the safety of the system, and to make sure that you don't inadvertantly do something bad when you just meant to do something harmless.

However, when you prefix your command with "sudo ", it tells the system that you know the command is something only the *root* user can perform. Basically: If it won't let you perform a certain command, prefix it with "sudo".

Windows has a similar feature, but funnily enough only Linux users actually know about it. In Windows, create a limited user account (non-administration). Log in as this account, now right-click on one of the programs on your desktop and choose "Run As...". In the box that appears, tell Windows to run the program as another user - your usual administration account.

The Windows "Run As" command has been badly implemented, so don't worry if you have problems with programs being run in this way. Sudo will always work though.

EDIT: I don't have Apache on my computer anymore, but I think there's a setting in a file in /etc/apache2 to change the "server root" (the directory which contains the web site). You will need to run something like this:

```
sudo nano /etc/apache2/apache2.conf
```

---

### Post by slimdog360 on 2006-10-08
[http://www.ubuntuforums.org/showthread.php?t=260731]("http://www.ubuntuforums.org/showthread.php?t=260731")

---

