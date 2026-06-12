---
title: "Help With Installation I Am New"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by GILBERTO15 on 2006-12-31
i am new to linux, so i dowloaded the ubuntu 6.06 for the power pc, i have an ibook, everything went well. So it asks u for the login, i gave it my login and then a password. After that it show something called sudo man root, i dont know what to do from here. the adminstrator is Gilberto, the username is Gil and the password is Alanis, but it never asked for a Adminstrator password in the basic installation please help me.

---

### Post by nalmeth on 2006-12-31
I would guess that you are sitting in a virtual terminal, because thats the first message you get when you open one. You're supposed to be in the desktop environment. For some reason you aren't and we have to find out why. When you enter these commands, try to record the output of errors that come up. You don't need to write down every last thing, just things that seem the most critical against the Desktop starting up.

What happens when you enter:
startx

or 

sudo /etc/init.d/gdm restart

EDIT: By the way, you didn't install the server edition did you? It doesn't come with GUI. To install the GUI you would enter:
sudo aptitude update
sudo aptitude install ubuntu-desktop

---

### Post by GILBERTO15 on 2006-12-31
linux boots up saying hardrive ok, linux ok and disk ok, and some other things, so its a black screen with white letters saying GIlbertologin:, then after login passwd:, when i enter everything it show last time login and the sudo man root thing, now it something like this gil$ubuntu:, how do i get to run the opertaing system not the command thing.

---

### Post by GILBERTO15 on 2006-12-31
i installed the server type

---

### Post by riven0 on 2006-12-31
> **GILBERTO15 said:**
> linux boots up saying hardrive ok, linux ok and disk ok, and some other things, so its a black screen with white letters saying GIlbertologin:, then after login passwd:, when i enter everything it show last time login and the sudo man root thing, now it something like this gil$ubuntu:, how do i get to run the opertaing system not the command thing.

It doesn't look like you get any errors, which means you probably have the server edition. Did you try installing the desktop like nalmeth said to?

> 
sudo aptitude update && sudo aptitude install ubuntu-desktop

---

### Post by GILBERTO15 on 2006-12-31
what is the gui

---

### Post by riven0 on 2006-12-31
> **GILBERTO15 said:**
> what is the gui

GUI = Graphical user interface

---

### Post by tmatt95 on 2006-12-31
Hiya,
> **GILBERTO15 said:**
> what is the gui
GUI stands for Graphical User Interface and is a way by which the computer displays information to  you, when you are using it. There are a number of different ways by which the computer can show the user information, including command line (the user types in the commands by hand, Ms Dos is an example) and menu driven.  

I would recommend downloading the desktop CD and using that, as that is set up in a way that is a lot more user friendly for the Linux novice like you and me. If you have any problems feel free to post them on the forum and we will be more than happy to help.

Regards,
Matt :-D

P.S Sory riven0 for repeating you. It serves me right for spending to long with the reply *doh*.

---

### Post by riven0 on 2006-12-31
> **tmatt95 said:**
> 
P.S Sory riven0 for repeating you. It serves me right for spending to long with the reply *doh*.

Hehe... happens to me all the time. :)

---

### Post by nalmeth on 2006-12-31
Or in a personally relevant context, its your desktop, mouse, and all the graphical applications.

The server edition doesn't come with a GUI, because most linux server admins just use command line tools, and don't need the extra baggage that comes with the desktop.

To get your desktop, please, just run the command we've given you, and you'll find out what we mean.

sudo aptitude update && sudo aptitude install ubuntu-desktop

Reboot the computer and you'll get what you probably expected when you started.

---

### Post by GILBERTO15 on 2006-12-31
gonna pick up my computer left it at work,

---

### Post by GILBERTO15 on 2006-12-31
so i entered sudo aptitude update and it shoed reading packages done building done intiaizing pakages done, so next i enter sudo aptitude install ubuntu-desktop and it shows timestamp too far in the future: feb 24 15:23:47 1970, so then i tell the computer to reboot it show must be superuser?

---

### Post by riven0 on 2006-12-31
> **GILBERTO15 said:**
> so i entered sudo aptitude update and it shoed reading packages done building done intiaizing pakages done, so next i enter sudo aptitude install ubuntu-desktop and it shows timestamp too far in the future: feb 24 15:23:47 1970, so then i tell the computer to reboot it show must be superuser?

1970? :confused: 

No, sudo will work like superuser. Alright, why don't you try apt-get instead of aptitude:
> 
sudo apt-get update && sudo apt-get install ubuntu-desktop

---

### Post by GILBERTO15 on 2006-12-31
so i put in sudo aptitude install ubuntu-desktop and it said no desktop installed, now is there any other ubuntu download for power pc that i can try which wont be so compicated

---

### Post by GILBERTO15 on 2006-12-31
during the installation do u have to be connected to the internet? because i wasn't

---

### Post by riven0 on 2006-12-31
> **GILBERTO15 said:**
> during the installation do u have to be connected to the internet? because i wasn't

hehe... yeah, you gotta be connected since your downloading from the official repositories. Just plug in the ethernet cable or something and Ubuntu should detect it.

---

### Post by GILBERTO15 on 2006-12-31
What Other Type Of Ubuntu Should I Download Which Isn't So Complicated

---

### Post by benerivo on 2006-12-31
Download the full live cd iso (it will be around 700MB) from your nearest location...
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)

---

### Post by GILBERTO15 on 2006-12-31
So I Installed It Again With The Internet Connection And I Entered The Commmand Sudo Aptitude Install Ubuntu-desktop And It Began Writing For 1o Minutes Then I Reboot The Computer And I Am Still At This Command Thing Not The Desktop Stuff

---

### Post by GILBERTO15 on 2006-12-31
The Username Is Gilberto And The Login Is Gil, After Logging In It Show Gil@gilberto:~$ So I Enter Sudo -i And I Get Root@gilberto:~# And I Enter Sudo Aptitude Install Ubuntu-desktop I Wait There For 10 Minutes And Then The Aptitude Update, Then After That I Enter Reboot And The Computer Reboots, I Am Still Stuck At This Command Screen Please Help Me

---

### Post by riven0 on 2006-12-31
When you did sudo aptitude install ubuntu-desktop, did it start downloading stuff? It should take a good 20 to 30 minutes, depending on your connection, to get the desktop downloaded and installed. If it ended with an error, post it here so we can look over it. 

BTW, when you restart your comp, don't just hit the power button. Restart it with:

> sudo shutdown -r now

Oh, and you don't have to be root to get the desktop installed. That's what sudo is for. :)

---

### Post by nalmeth on 2007-01-01
It is evident that you are frustrated, I can understand this. I'm sorry it has been so difficult, but bear with us, we will keep trying to help you.

You actually DON'T need the internet connected to install the desktop environment, only to get extra non-essential packages, and updates.

The timestamp thing is very odd, since I haven't encountered it myself, I don't know what causes it. 

From what I understand, you've now downloaded the desktop CD, and installed it.

When you get to the command prompt, do any errors appear?
When you run 
```
sudo aptitude install ubuntu-desktop
```Does it tell you that you have 0 packages to upgrade/install? 

Just to be sure, lets run these commands, to make sure EVERYTHING is up to date:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo aptitude dist-upgrade
```Now try,
```
startx
```Which will try to start the X server, and the desktop environment, running as your current user. If there are any errors here, please let us know the details. 

Normally, everything should be running fine now. If there are errors, it is possible that the video driver selected by the installer for your computer isn't working properly. 

To correct this, we can try a generic video driver that should work on all cards. You won't have 3D-acceleration with this VESA driver, but it should get you going in 2D.
To run a video configuration wizard, enter:
```
sudo dpkg-reconfigure xserver-xorg
```Please patiently answer the questions by hitting enter, until you get to video driver. At this step, select VESA.

Just hitting ENTER will pick the default suggestion for you hardware, for all other options, it will be safe. Take your time anyway if you would like to see the details.

I hope this information helps you to use Ubuntu

---

### Post by Frak on 2007-01-01
You shouldn't install something when you are root like...
```
sudo -i
```
for one that can cause a timestamp error, when it looks at the root folder and reads the production info., but thats far off the point.

You shouldn't install something as root, but as sudo instead, if you install something as root, it may not start unless you're root.  This doesn't have much to do with your problem, but when its solved, it'll make since later.

---

