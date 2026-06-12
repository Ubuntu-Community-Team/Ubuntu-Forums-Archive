---
title: "Need Help -Several Things"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by skullmasher on 2007-04-29
I'm pretty new to Ubuntu and Linux in general. Ive been doing alright so far but now Ive run into some problems that I cant seem to find the answers through research. Im just going to list the course of events im trying to accomplish and the problems along the way, and maybe you can help with some of them:

~As of now the main goal is install my Nvidia drivers, and I came here [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1)

      I have dapper by the way and a GeForce 6 series

~I proceeded to download the coresponding dirver.  So im wondering exactly how should I install it?

~I continued to read that wiki and got to where it says to enable the Universe/Multiuniverse repositories What is a repository? How do i enable them? What will these specific ones do?

~I have wine installed and have used it succesfully already, as I discovered the need         to install my nvidia drivers when I thought about playing games on Ubuntu.

~I read some more stuff about enabling repositories and found that after they are enabled I should install them from Snyaptic??

~I then read that I should type this into the terminal : /etc/apt/sources.list , In order to get the list of my current repositories, but this is where I was halted and came here, It then says : bash : /etc/apt/sources.list : Permission denied.  ??? Cluelesss on that but it is most likely simple. 

~Thanks to anyone who can help, I apreciate it alot.

---

### Post by Wiebelhaus on 2007-04-29
[Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

this thing rocks.

---

### Post by riminicat on 2007-04-29
Look into using the terminal to get and install things, once you know how to use it, its a lot easier

---

### Post by skullmasher on 2007-04-29
~I'll look at envy. Thanks
~Yes im begining to see the power witheld by the terminal. Thanks

---

### Post by Nythain on 2007-04-29
as for your driver issue... find out if you need the regular or the legacy, i think you should be fine with the regular. Did you download the .run file from nvidia's site or do you plan on installing from the repositories (probably the better idea)

repositories are servers where a bunch of software for ubuntu sit waiting for you to download and install through either synaptic (in gui) or apt-get in terminal.

you can see a list of them by opening the /etc/apt/sources.list with a text editor... from terminal type sudo (or gksudo, not sure if gedit is a gui app) gedit /etc/apt/sources.list 

you enable the multiverse/universe by uncommenting the server addresses that have a # in front of them... or it can be done inside of synaptic also i believe, though im not sure how off the top of my head

the terminal will end up being your friend, for the reasons of 1. some things you can only run in console (well you can run them from you de once you get good at making menu entries and writing bash scripts and the like) and 2. when you run something in terminal, you have better access to any errors it might give, for helping in solving problems

---

### Post by John.Michael.Kane on 2007-04-29
Step one open the terminal. all these commands are run from the terminal.

Click on Applications--->Accessories--->Terminal

Run this:
```
gksudo gedit /etc/apt/sources.list
```

[COLOR="Red"]Make sure you sources.list looks like the one below[/COLOR]
	
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

After making sure everything matches the above run this command **gksudo aptitude update**


Part Two: installing the driver.

Next run this:
```
uname -r
```

Should return something like this: 2.6.15-25

Now run:
gksudo aptitude install linux-(place your architecture here) 386, 686, k8,

Install the Nvidia driver:
```
gksudo aptitude install nvidia-glx
```

Enable the driver in your xorg:
```
gksudo nvidia-xconfig
```

Create a link to the “Nvidia-Settings” Panel in your application menu: Note: An empty file will open after running this
```
gksudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Paste the following lines into the new file:
```
[Desktop Entry] Name=NVIDIA Settings Comment=NVIDIA X Server Settings Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;
```

Save the edited file.

CTRL+ALT+BACKSPACE

Your done.

---

### Post by skullmasher on 2007-04-29
Ok i did what SD said and it seems to be working fine and everthing is installed correctly. But just one question: What did CTRL ALT Backspace do?

---

### Post by John.Michael.Kane on 2007-04-29
> **skullmasher said:**
> Ok i did what SD said and it seems to be working fine and everthing is installed correctly. But just one question: What did CTRL ALT Backspace do?

Ctrl-Alt-Backspace restarted xorg with out having to reboot the machine.

---

### Post by skullmasher on 2007-04-29
Ok thanks

---

