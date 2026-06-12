---
title: "graphical user interface"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-05-21
Hello 

I intalled ubuntu on my laptop and it seems to be working fine except for the graphical user interface all i have is the command line is there something i can do about that?

Thanks

---

### Post by richbarna on 2006-05-21
It sounds like you did the "server" install which is the base Ubuntu, or if you did install it normally, you just have to log in put your password + enter.
Then type :-
> startx
If nothing happens, post back and i'll show you how to install KDE or GNOME
Good Luck !:)

---

### Post by ckonrad on 2006-05-21
ok thanks i will try the startx command however it says that x server didnt start properly. I am pretty sure i did the regular installation not the server but i will check.

Thank you

---

### Post by ckonrad on 2006-05-21
yeah i just got the same error that x server didnt start properly and asked me if i wanted to view the error messages. I

---

### Post by richbarna on 2006-05-21
Ok, what laptop have you got? Processor/RAM etc.
And what is the graphics card ? (sounds like ATI)

---

### Post by mlind on 2006-05-21
make sure you have necessary desktop software installed

```

sudo apt-get update && sudo apt-get install ubuntu-desktop

```

If ubuntu-desktop was already installed, post your gfx-card info.
You can search forums using keyword 'dpkg-reconfigure xserver-xorg',
because that's probably the next thing you're going to have to do.

---

### Post by ckonrad on 2006-05-21
i have mobile AMD sempron 3000+ 787MHz, yes i do have an ATI Radeon express 200m. Ram is 640MB. My laptop is a Compaq less than a year old. I installed onto my desktop with the same disk anc it worked fine so i know that the disk i have works and has everything i need to run ubuntu. I did the regular default installation.  just tried a reinstall and it does the same thing i just get the failed to start x server message.

THanks

---

### Post by ckonrad on 2006-05-21
Yeah i did that and i searched for information on how to configure x server but all i got was information on how to configure a server, is there a specific page on how to configure x server for the type of problem i am having. Or maybe i should just download gnome or some other desktop to use.




[QUOTE=mlind]make sure you have necessary desktop software installed

```

sudo apt-get update && sudo apt-get install ubuntu-desktop

```

If ubuntu-desktop was already installed, post your gfx-card info.
You can search forums using keyword 'dpkg-reconfigure xserver-xorg',
because that's probably the next thing you're going to have to do.[/QUOTE]

---

### Post by richbarna on 2006-05-21
Ok, this happened with my Toshiba Satellite,
I would try installing the "server" only, basic install, and then go for installing the desktop afterwards. This worked for me.
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kde
or
> sudo apt-get update && sudo apt-get install kde

You can go for the Ubuntu Gnome or KDE desktops,
I personally find KDE faster and better looking ;)
Good Luck

---

### Post by mlind on 2006-05-21
If you're having problems reconfiguring X-Server is a common solution.
switch to tty1 (Ctrl+Alt+F1) and login.


```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo dpkg-reconfigure xserver-xorg
(try with 'vesa' driver if 'ati' doesn't work)
sudo /etc/init.d/gdm restart

```

for ATI card, see [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by ckonrad on 2006-05-21
actually there is someone on the forum with the same laptop as me that got it working using this below i think i got it figured out.

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #select the "vesa" module

wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)
(this will download the ati driver from the ati website)

sudo apt-get install gcc-3.4 module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
cd directory of ati driver
chmod +x ati-driver-installer-8.24.8-x86.run
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb

sudo rm /usr/src/fglrx-kernel*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

reboot

---

### Post by mlind on 2006-05-21
if you want to manually install ati driver that's okay too :)
There's a package for already compiled ati driver though.

---

### Post by ckonrad on 2006-05-21
The thing with the below method of solving my graphics cards issue is that i have to connect to the internet and download those drivers i cant seem to get my network configured during installation. Where do i start to solve that problem?


[QUOTE=ckonrad]actually there is someone on the forum with the same laptop as me that got it working using this below i think i got it figured out.

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #select the "vesa" module

wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)
(this will download the ati driver from the ati website)

sudo apt-get install gcc-3.4 module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
cd directory of ati driver
chmod +x ati-driver-installer-8.24.8-x86.run
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb

sudo rm /usr/src/fglrx-kernel*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

reboot[/QUOTE]

---

### Post by mlind on 2006-05-21
[QUOTE=ckonrad]The thing with the below method of solving my graphics cards issue is that i have to connect to the internet and download those drivers i cant seem to get my network configured during installation. Where do i start to solve that problem?[/QUOTE]

you should probably open a new thread about non-working network connection.

---

### Post by ckonrad on 2006-05-21
ok i'll do that but first, i got x server to work basically but i cant change screen resolutions so i downloaded the drivers from my desktop and put them on my laptop with a flash driver. Now when i try to install those drivers it says i need to install them as the super user. How do i do that?




[QUOTE=mlind]you should probably open a new thread about non-working network connection.[/QUOTE]

---

### Post by mlind on 2006-05-22
[QUOTE=ckonrad]ok i'll do that but first, i got x server to work basically but i cant change screen resolutions so i downloaded the drivers from my desktop and put them on my laptop with a flash driver. Now when i try to install those drivers it says i need to install them as the super user. How do i do that?[/QUOTE]

I didn't quite understand what you're doing here, but when you need to do
something as 'super user' or 'root', use *sudo* or gksu for graphical password
prompt.

syntax is *sudo command*

---

### Post by ckonrad on 2006-05-22
yeah triied that and it just says "Sudo command not found"

I also tried using the gksu and it told me i had the wrong password when i typed in the right one, i had to type that password to get into ubuntu so i know what my password is. I used this same disk to install on my desktop so i know that it isnt a problem with the cd i have. It works great on my desktop. I didnt need to configure anything at all. 



[QUOTE=mlind]If you're having problems reconfiguring X-Server is a common solution.
switch to tty1 (Ctrl+Alt+F1) and login.


```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo dpkg-reconfigure xserver-xorg
(try with 'vesa' driver if 'ati' doesn't work)
sudo /etc/init.d/gdm restart

```

for ATI card, see [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)[/QUOTE]

---

### Post by mlind on 2006-05-22
[QUOTE=ckonrad]yeah triied that and it just says "Sudo command not found"

I also tried using the gksu and it told me i had the wrong password when i typed in the right one, i had to type that password to get into ubuntu so i know what my password is. I used this same disk to install on my desktop so i know that it isnt a problem with the cd i have. It works great on my desktop. I didnt need to configure anything at all.[/QUOTE]

commands you're using are case-sensitive, you did write commands with
lower-case letters right?

for example
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by mlind on 2006-05-22
and that you're able to perform sudo tasks in normally configured Ubuntu,
you must belong to group called 'admin'.

type command *groups* on terminal to find out the groups you're on.

---

### Post by ckonrad on 2006-05-22
yeah i used lower case letters, i also tried running the ati drivers from root by going to the 'run as different user option' and it just tells me i have the wrong password all the time, just like when i used gksu. When i type something like 'sudo apt-get install' and then the name of the file, its says that sudo is not recognized as a command like it doesnt exist, i never created any other passwords other than the one to get into ubuntu which was created during installation. So i dont know what password its asking me for caps lock is off i typed it in correcltly over a dozen times and it just keeps telling me the same thing over and over. So i have no idea what the problem is.

[QUOTE=mlind]and that you're able to perform sudo tasks in normally configured Ubuntu,
you must belong to group called 'admin'.

type command *groups* on terminal to find out the groups you're on.[/QUOTE]

---

### Post by mlind on 2006-05-22
[QUOTE=ckonrad]yeah i used lower case letters, i also tried running the ati drivers from root by going to the 'run as different user option' and it just tells me i have the wrong password all the time, just like when i used gksu. When i type something like 'sudo apt-get install' and then the name of the file, its says that sudo is not recognized as a command like it doesnt exist, i never created any other passwords other than the one to get into ubuntu which was created during installation. So i dont know what password its asking me for caps lock is off i typed it in correcltly over a dozen times and it just keeps telling me the same thing over and over. So i have no idea what the problem is.[/QUOTE]

hmm. I hope it's just invalid $PATH variable, so shell environment
cannot find sudo..

does command *whereis sudo* output it's location?
could you also give the ouput of *groups* command

---

### Post by ckonrad on 2006-05-22
[QUOTE=mlind]hmm. I hope it's just invalid $PATH variable, so shell environment
cannot find sudo..

does command *whereis sudo* output it's location?
could you also give the ouput of *groups* command[/QUOTE]

well it looks like its on my system from whereis sudo i got
sudo: /usr/bin/sudo /usr/bin/x11/sudo /usr/share/man/man8/sudo.8.gz

from groups i got
groups: adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

all i am trying to do is install the driver files so i can get my desktop to look normal, right now its bent and stretched all over the place. Hopefully these drivers will solve that issue.

---

### Post by mlind on 2006-05-22
[QUOTE=ckonrad]well it looks like its on my system from whereis sudo i got
sudo: /usr/bin/sudo /usr/bin/x11/sudo /usr/share/man/man8/sudo.8.gz

from groups i got
groups: adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

all i am trying to do is install the driver files so i can get my desktop to look normal, right now its bent and stretched all over the place. Hopefully these drivers will solve that issue.[/QUOTE]

ok, looks just like it should so far.
how about output of
*echo $PATH*

it should be something like
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

if that entry contains /usr/bin, where sudo is located - then everything looks okay,
and you're doing something wrong when typing that sudo command.

---

### Post by ckonrad on 2006-05-22
ok i'll try that in a minute but just for the record what am i supposed to type in to install these drivers exactly? i mean you dont need to put the file name i can fill in the blank, isnt it sudo apt-get install and then the file name? thats what i am typing in and that doesnt work, it asks me for my password and then  put my password in and it gives me an error saying i have the wrong password there is no reason for the password error i am using my correct password unless there is some default system password that comes with ubuntu other than the one i created. i think the reason i was getting the sudo error is because i typed in just sudo install instead of sudo apt-get install. Is there a specific place my file is supposed to be in in order for that command to work properly i have the file on my desktop right now. 


[QUOTE=mlind]ok, looks just like it should so far.
how about output of
*echo $PATH*

it should be something like
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

if that entry contains /usr/bin, where sudo is located - then everything looks okay,
and you're doing something wrong when typing that sudo command.[/QUOTE]

---

### Post by ckonrad on 2006-05-22
yeah thats exactly what it says when i type echo $PATH.

I dont i think i need to go through a basic intro to linux again i cant even do basic things in this os like moving a file it tells me i dont have permission to do it and i have no idea how to change permissions or anything. Its going to take me awhile to get used to this.


[QUOTE=mlind]ok, looks just like it should so far.
how about output of
*echo $PATH*

it should be something like
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

if that entry contains /usr/bin, where sudo is located - then everything looks okay,
and you're doing something wrong when typing that sudo command.[/QUOTE]

---

### Post by mlind on 2006-05-22
okay, so everything is in order afterall. What about if you go check that link
I posted on reply #10 and install that precompiled Ati binary driver using
apt-get? It should be very easy task to do.

---

