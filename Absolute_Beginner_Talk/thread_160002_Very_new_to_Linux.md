---
title: "Very new to Linux"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Mark Smith on 2006-04-13
I am trying to get into the world of Linux. I have downloaded ubuntu and installed in one of my desktop computer. After finishing the installation, I booted the computer. 

A shell screen appeared and asked me to logon. I gave my user ID and password correctly. Now the prompt is there. What should I do now? How should I run the GUI on it? Please help.

---

### Post by Sutekh on 2006-04-13
At the main installation screen did you just press Enter or did you type server/expert then Enter?

If you did a server install then you didn't install a desktop environment.  Now you will have to choose one to install.   You can choose GNOME, KDE or XFCE

Have a look at this site, and click on the Desktops at the bottom for some screenies on these environments, and maybe you can decide what you want.

[http://xwinman.org/]("http://xwinman.org/")


If you want [GNOME](www.gnome.org) - Default Ubuntu Desktop, I'd use this command
```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.

If you want [KDE](www.kde.org) - Most Common Linux Desktop, I'd use
```
sudo apt-get install kubuntu-desktop
```

If you want [XFCE](xfce.org) - very light desktop, I'd use
```
sudo apt-get install xubuntu-desktop
```

These commands will install the respecitve desktops with most of the basic programs you will need.

---

### Post by Mark Smith on 2006-04-13
Thanks Suthekh for your help!

I have just pressed enter while installation; not chose Server. I am going to install GNOME as per code provided by you. As I am working on Linux for the first time. I dont know even how to list the directory. I will post back after installation of GNOME.

---

### Post by johnc4510 on 2006-04-14
Did you manually boot the computer when the install cd ejected? I ask this because the install usually ejects the cd, then it reboots itself and finishes installing the rest of the packages. If you did not let it finish installing all this, you probably need to start over because the install is not complete.
There should be no shell, after the install finishes, it will take you right to the login screen.

---

### Post by Mark Smith on 2006-04-14
Yes, John I did it. I left it for whole night and slept. In the morning when I am seeing to it, it is giving this prob.

---

### Post by Mark Smith on 2006-04-14
I tried  to install sudo apt-get install ubuntu-desktop command, it is showing that there is some problem in configuration and you have to run this command - "dpkg --configure -a"
But when I am running it, it is saying that  you have to provide super user password, but I dont have any. During installation it didnt asked me.

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=Mark Smith]I tried  to install sudo apt-get install ubuntu-desktop command, it is showing that there is some problem in configuration and you have to run this command - "dpkg --configure -a"[/quote]
sudo dpkg --configure -a (see below)
[QUOTE=Mark Smith]
But when I am running it, it is saying that  you have to provide super user password, but I dont have any. During installation it didnt asked me.[/QUOTE]
try this one as well (if above does NOT work): 
```
sudo dpkg-reconfigure xserver-xorg
```
accept defaults (unless yo know any better). when it says "choose a driver" (there is ati and vesa in the list), choose vesa. You'll figure out what video card driver you need later. 
As far as I remember, once you finish with the prompts, type "startx" and gnome should start. the command might as well be ```
/etc/init.d/gdm start
```
not sure

the superuser (root) password is the password you entered for yourself during installation. If you never entered any passwords, I would just do the installation from the beginning. It usually takes 30 minutes anyway.

---

### Post by dermotti on 2006-04-14
sudo dpkg --configure -a

---

### Post by Mark Smith on 2006-04-14
Thanks for the help. I think there must be some problem with installation. I am reinstalling it. But during installation ubuntu does not ask for any password for superuser. It just create an account and password that is certainly not the superuser. How will I get the super user password?

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=Mark Smith]I am reinstalling it[/quote]
I didn't wanna say it (bc it's depressing) but Iwould do the same. 
[QUOTE=Mark Smith]It just create an account and password that is certainly not the superuser. [/QUOTE]
that password is your superuser password. for more info, take a look at wiki.ubuntu.com/RootSudo.

Basically, you use the password you provided in 2 instances:
1. during login to gnome (type username and password in initial login)
2. using sudo (issuing commands with superuser/root privileges). 

Once you login to gnome, nothing non-administrative is supposed to ask for password (for example: networking and synaptic are administrative and will ask password, firefox is non-administrative and will not ask for password). 

networking: System>Administration>Networking (configuring network)
synaptic: System>Administration>Synaptic (package management, installing and uninstalling software)

---

### Post by Mark Smith on 2006-04-14
[QUOTE=towsonu2003]I didn't wanna say it (bc it's depressing) but Iwould do the same. 

that password is your superuser password. for more info, take a look at wiki.ubuntu.com/RootSudo.[/QUOTE]

Thanks for the info! Getting feel ](*,)  of Linux (ubuntu) now!

---

