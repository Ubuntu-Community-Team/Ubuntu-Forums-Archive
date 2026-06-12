---
title: "Lost Noob"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by thecresta on 2006-09-10
Hi all,

I'm completely new to Linux, and wondered if somebody can point me in the right direction regarding the following:

1) I'm used to working in a DOS environment, but the 'command prompt' side of  Ubuntu looks a fair bit different. Does somebody know where I can get a list of common commands? Also, out of curiosity, is Ubuntu primarily a GUI OS like XP, or like Windows 9x/Me with a GUI built on a DOS-based OS?

2) I don't seem to be able to modify files on the 'file system' drive. Even though I only have one user set up (OEM by default), I do not have permission to edit anything. I say this because my sources.list in my /etc/apt/ folder has corrupted. I know how to fix it, but I can't save the changes.

3) Is there any software that anybody would recommend?

Thanks for any help!
Andy

---

### Post by lukew on 2006-09-10
Hi thecresta,

Check out this; will get ya started!

[http://yolinux.com/TUTORIALS/unix_for_dos_users.html](http://yolinux.com/TUTORIALS/unix_for_dos_users.html)

linux kernel is like dos gnome is like windws 32. BTW xp 95,96 me 2000 etc were all operating system in their own right, unlike dos/windows32.

You need to have write permission to modify files. If you dont have write access you need to ask why. If this is a system file you need to configure sudo to gain temp root access, otherwise think about changing the ownership of the permission with chown and chomod.

Check out [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) and use the ubuntu wiki and the forums howtos. V Valuable. 

There is alos an application conversion chart to help you decide which application in linux is the windows equivalent.

Luke

---

### Post by mbmccormick on 2006-09-10
1) Ubuntu is based in Linux, which is based on Unix, which was primarily command prompt, or "terminal" based. So Ubuntu does have a terminal foundation, but is primarily a GUI. I'm concerned as to why you haven't noticed the GUI yet. As of commands, just search google for "common linux commands" or "common unix commands".

2) When using Linux or Unix, there are many users installed. You being one, and also root, and other users that unix uses... Root is the super user. Root has control over everything, permission to edit everything. It can do anything. You, OEM only have permissions on your home directory and some public ones. But root has permission for all. So if you want to edit your sources file, type this "sudo gedit /etc/apt/sources.list" at the terminal. sudo means superuser do. it runs a command as root, which requires a password. gedit will open up the gnome text editor.

---

### Post by bulldog on 2006-09-10
Linux is not DOS.

You installed the alternate cd and you have to make an user account,but I can't tell you how or what,I used the live cd.
But someone can and will come by and save you.

Look here for info about Linux and its filesystem.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Najand on 2006-09-10
> **thecresta said:**
> 
2) I don't seem to be able to modify files on the 'file system' drive. Even though I only have one user set up (OEM by default), I do not have permission to edit anything. I say this because my sources.list in my /etc/apt/ folder has corrupted. I know how to fix it, but I can't save the changes.


I think you need to type
```
sudo
```
before your commands related to system settings (Admin Tusks). It will ask for your password then and you should type yours afterwards.

---

### Post by monktbd on 2006-09-10
hi and welcome to linux :)

> **thecresta said:**
> 
1) I'm used to working in a DOS environment, but the 'command prompt' side of  Ubuntu looks a fair bit different. Does somebody know where I can get a list of common commands? Also, out of curiosity, is Ubuntu primarily a GUI OS like XP, or like Windows 9x/Me with a GUI built on a DOS-based OS?


actually a linux distirubtion is a heterogenous mixture of a hell lot of programs.

you have the commandline interface, where a comparison to DOS is quite an insult, the only thing that is similar is the looks.
the command line interface is really really powerful and getting to know all that you can do with it takes quite a long time and i lear something new every day as well.

the way linux usually delivers its programs is that you have a lot of small commandline tools that can do the most magical things when used properly. that is often quite a tedious and awkward procedure so there is the x-server with window managers and desktop environments (like gnome, kde, xfce) to make life a bit easier.
a lot of the gui programs available actually use the underlying command line tools to accomplish the task. it is just easier sometimes to set all the needed switches with a gui than with the cli.

i just googled for a bash command listing
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
but there are quite a few very often used commands missing simply because they are distribution dependant (e.g. apt-get)

> 
2) I don't seem to be able to modify files on the 'file system' drive. Even though I only have one user set up (OEM by default), I do not have permission to edit anything. I say this because my sources.list in my /etc/apt/ folder has corrupted. I know how to fix it, but I can't save the changes.


please read about sudo/su/root account and how ubuntu approaches it.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> 
3) Is there any software that anybody would recommend?


name certain things you want to do and we likely can tell you what we use to do it. :)

---

### Post by Omnios on 2006-09-10
There are some usefull links in my signature including a thread with multiple command line commands ranging from quick reference to little tutorials

---

### Post by thecresta on 2006-09-10
Wow! I wasn't expecting such a huge response so quickly! 

I do boot into the GUI, but I could see on this forum that the CLI/terminal is the big thing in Ubuntu. I can work DOS, but I hear it's a very weak OS compared to UNIX. Hey, what do you expect? MS/BG bought DOS off a lone programmer for a couple of thousand bucks! The origins of a multi-billion $ empire... ;)

I've tried "sudo gedit /etc/apt/sources.list", but it responds with 'cannot open display (null)'. Am I doing something wrong? I apologise if one of the links provided has this information, but I haven't had time to read through them all yet. They are all bookmarked, though! 

Oh, and before I forget, you're right about the alt cd bulldog - it was taking far too long to install using the live cd - I had a lot of partitions to set up and it took 10-20 minutes to get from one menu to the next. Ubuntu is pretty fast now though. Strange.

Thank you all! This is exactly what I was looking/hoping for!

---

### Post by IYY on 2006-09-10
> I've tried "sudo gedit /etc/apt/sources.list", but it responds with 'cannot open display (null)'. Am I doing something wrong? I apologise if one of the links provided has this information, but I haven't had time to read through them all yet. They are all bookmarked, though!

'sudo' is used for terminal commands. If you want to run a graphical program as superuser, use 'gksudo' instead.

---

### Post by CarpKing on 2006-09-10
> **thecresta said:**
> I do boot into the GUI, but I could see on this forum that the CLI/terminal is the big thing in Ubuntu. 

Not sure if you have noticed this yet, but in the GUI there is a program called the terminal.  The commands you see all over the forums can be typed into the pure CLI, but most people use the terminal for this purpose, without leaving the GUI.  Most of these tasks can also be accomplished through purely GUI methods, but it is much easier to simply give the commands than to explain where in the menu structure the buttons and whatnot are located.

---

