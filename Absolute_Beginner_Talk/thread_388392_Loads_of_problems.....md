---
title: "Loads of problems...."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by 7llusion on 2007-03-19
I've recently switched from Vista to Ubuntu(!), but I'm wondering if I amde the wrong choice, I've had loads of problems:
-I simply cannot change the screen resolution I am stuck at 640x480@60 Hz
-I cannot write to the filesystem hard disk, in proprieties > permisions , I cannot allow write or execute for any kind of user("The permission could not be changed"), I am only able to make folders on the desktop
-I tried installing NDISWRAPPER, but I can't find how to execute the comand lines that are required(make uninstall, make, ake install) I'm trying to install this driver:
[http://www.3com.com/products/en_US/result.jsp?selected=5&sort=effdt&sku=3CRWE254G72&order=desc](http://www.3com.com/products/en_US/result.jsp?selected=5&sort=effdt&sku=3CRWE254G72&order=desc)
Thats's all^^.
Illusion
PS:
I've got:
-Intel Pentium D, Dual Core
-3CRWE254G72 3co USB wireless adapter
-775Twins-HDTV Asrock motherboard
I'm sure Ubuntu can be a wonderful thing, but for the moment it's only a problem for me

---

### Post by finferflu on 2007-03-19
For ndiswrapper, you can give a look at this guide: [http://www.ubuntuforums.org/showthread.php?t=329299](http://www.ubuntuforums.org/showthread.php?t=329299)

It's not for your card, but the procedure is the same (apart from blacklisting, I'm not really sure about it, but you can skip it).

Good luck for the rest!

---

### Post by Zzl1xndd on 2007-03-19
For the screen res use the terminal and enter sudo dpkg-reconfigure xserver-xorg it will ask you for your password and walk you threw setting up your Video settings if you dont know an answer to one of the questions just pick the defualt and go on. There will be a point when it asks what Screen res it should list pick the ones you want and continue.

Just so I understand are you not able to write to your home folder?

---

### Post by taylonr on 2007-03-19
On your filesystem,

copy and paste what your /etc/fstab file displays (you could do gedit /etc/fstab and it will come up in an editor like notepad on windows.)

This file is **f**ile **s**ystem **tab**le  it shows how all of your devices are loaded and with what permissions they are loaded at boot up.

---

### Post by AtrejuT on 2007-03-19
Welcome to Ubuntu!

lets tackle one after the other:
your resolution: do you know what graphics card you are using?
Which version of ubuntu do you use? Edgy?

Filesystem: You can not change anything on the / filesystem - basically that's a security feature. You can do anything you like by becoming super user (the command on the console is 
```

sudo realcommand

```
but for the time being you should be really careful with that, until you know a little more about how things work. You should stick to your home directory, i.e.
/home/yourusername
you have permissions set to do whatever you like there, and that is the place where you should store all your documents etc.

ndiswrapper: Could you tell me what exactly you are trying to do? is there a guide you are following?

atreju

---

### Post by Nythain on 2007-03-19
being stuck at that craptastic resolution im going to assume you dont have the proper drivers for your video card installed... there are many good guides on this site and others for installing proprietary drivers for ati and nvidia cars, and the right search might turn up drivers for older or alternative display devices like onboard video and whatnot... 

writing to the disk is tricky... most folders you would need root access to write to... if installing something that requires that, or if you really MUST put something somewhere, i would suggest the sudo command, wich gives you temporary root access without actually loging in as root....

ndiswrapper i havent tried yet since im still wired into the network and most references i've for it are to get windows drivers working in linux for things like wireless cards and whatnot...

not sure if any of that helped... oh yeah, ./configure is usually a script contained in the folder of whatever you downloaded that you want to install... it creates a make file... make should be on your system, and make install to boot... if not, i forget what packages you would want to install, possibly build-essential, automake, etc... the defualt standard to install something from source would be to cd into its directory, ./configure then when thats done make then when thats done make install giving you had not errors during ./configure and make...

---

### Post by 7llusion on 2007-03-19
I can't write to my home folder,
and when I'm asked for my password, the keyboard goes completely dead for my terminal!
Illusion

---

### Post by LanDan on 2007-03-19
if you want to change the screen resolution you might want to have a look at the file /etc/X11/xorg.conf in the "screen" section.

you might find out that you can not change this file, so you have to do it as root (administrator)

just try something like this in the commandline
sudo gedit /etc/X11/xorg.conf

---

### Post by 7llusion on 2007-03-19
I can't do any sudo command because as I've already said my keyboard goes dead for the terminal application(can still use it in Text Editor) when I have:
Password:

---

### Post by AtrejuT on 2007-03-19
there is nothing shown behind the password prompt. Maybe this is confusing you. The keyboard still works even though nothing appears. Just enter your password and hit enter.

---

### Post by Adramelech on 2007-03-19
Your keyboard is not dead, when you are asked for the password, it doesnt show what your typing, not even '*' so just type your password and hit enter.

You are able to write to your home/user directory not your /home directory

---

### Post by benmoreassynt on 2007-03-19
You should be able to write to your home folder if you are logged in correctly.

The path in the filesystem is /home/yourloginname. If you are logged in as a different user you will not be able to write here. Since Desktop is a folder within your home folder, you must have write permissions somewhere.

But it sounds like you may be missing a few key Linux concepts.

Installing things like ndiswrapper (or anything else) should be done using Synaptic Package Manager. There's no reason why you would want to compile it using make - it will just be a world of pain.

Filesystem changes will need to be made when signed in with 'root' permissions. The properties/permissions should prompt for that though.

A lot of wireless cards work now without ndiswrapper, so make sure you need it before using it. It can be headache for new users.

I wouldn't mess about with fstab until you are sure you need to. Keep a backup of the old version.

For the other specific details, keep searching here - everything will be addressed somewhere.

Keep persevering.

---

### Post by 7llusion on 2007-03-19
Is there a dxdiag like command fro Linux to determine my graphics card, I've forgot the one I've got^^
Illusion

---

### Post by Zuuswa on 2007-03-19
entering the command:
```
lspci
```
into a terminal should output all of your hardware.

---

