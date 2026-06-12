---
title: "[SOLVED] Run Automatically at Startup"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by SneakPeak on 2008-02-18
Hi All,

How do I make things run automatically at startup / login?

I want to start samba automatically and I want to configure eth0.  At the moment once I have booted I type:

sudo ifconfig eth0 192.168.0.1

and

sudo /etc/init.d/samba start

Is the sudo necessary?  

How do I get these to run automatically on every startup?

Thanks

Adrian

---

### Post by Crooksey on 2008-02-18
Make a script in your home folder with the commands you want to launch..

```

chmod +x ~/script
```

Then....

Menu, system, prefrences, session

Then add new, under command put..

```

/home/<user>/<scriptname>
```

Then it will run your script at login.

---

### Post by ruy_lopez on 2008-02-18
if you install this:

```
sudo apt-get install sysv-rc-conf
```

Run this:

```
runlevel
```

remember the number:

```
sudo sysv-rc-conf
```

Then you can scroll down to samba (in the column revealed using runlevel) and enable 'X' by pressing space.

---

### Post by SneakPeak on 2008-02-18
Thanks Crooksey

I don't have peferences or session under menu, system???

Sneaks

---

### Post by Crooksey on 2008-02-18
Click system menu on gnome, then prefrences, then sessions.

In kde, edit the autostart file and place your commands in..

```

~/.kde/Autostart
```

Then..

```

chmod +x ~/.kde/Autostart
```

---

### Post by SneakPeak on 2008-02-18
Thanks Cooksey

I am running Kubuntu.  I have found /home/~/.kde/Autostart

Autostart in this case is a directory / folder not file.  Inside Autostart there is a .directory file.    The file contains a lot of different language versions of automatically start.

What do I do?  Do I create a new Autostart file here and make it executable?

Thanks

Sneaks

---

### Post by SneakPeak on 2008-02-18
So close and yet so far??

In Crooksey's post is Autostart a file or a directory?
Do I place an executable script in the Autostart directory or do I place a file calld Autostart in the Autostart directory and make it executable???

Please help

Thanks

Sneaks

---

### Post by Crooksey on 2008-02-18
Autostart is a file, put whatever commands you want to launch in the filem and then chmod +x it, example file

```

#~/.kde/Autostart
pidgin &
fusion-icon &
dhcpcd eth1 &

```

---

### Post by SneakPeak on 2008-02-19
Thanks Crooksey,

I am in the office on my work XP pc.  I'll give this a try this evening and post my success / failure.  

Cheers

Sneaks

---

### Post by hyper_ch on 2008-02-19
if you install samba, it should setup the server automatically to run at startup.

---

### Post by SneakPeak on 2008-02-19
Howdy Folks

I have another further problem.  I need to run the ifconfig command as root.  During a boot up I obviously can't type the root password.  How do I run the command as root inside the Autostart file?

Thanks

Sneaks

---

### Post by SneakPeak on 2008-02-19
> **hyper_ch said:**
> if you install samba, it should setup the server automatically to run at startup.

How do I check if samba is running? 

Sneaks

---

### Post by hyper_ch on 2008-02-20
try
```

ps aux | grep samba

```

or

```

ps aux | grep smb

```

---

### Post by ruy_lopez on 2008-02-20
Why do you have to run ifconfig at boot?

You should be able to put the commands in /etc/network/interfaces. What commands are you running? (/etc/network/interfaces uses slightly different syntax to ifconfig)

---

### Post by SneakPeak on 2008-02-25
Thanks Ruy

After reading your post I did a bit more searching on /etc/network/interfaces.  My file had only the following lines:

auto lo
iface lo inet loopback

I added the following lines:

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255

After this my eth0 interface loaded automatically at start up.  Another command that I found useful was:

/etc/init.d/networking restart

By using this I could edit the interfaces file and see what effect it had!

I have also noticed that firestarter runs in the background no matter what I do so as long as my eth0 and ppp0 are running my home network and internet connection sharing works.

Thanks for the help and sorry I was so slow to respond.  I have been away from the PC for a while.

Sneaks

---

### Post by parmdeep on 2008-02-25
How to add the source of Ubuntu Tweak

No matter your Ubuntu is Feisty, Gutsy or Hardy, open your terminal, type the command to run gedit(or other editor in your opinion) to modify the sources.list:

sudo gedit /etc/apt/sources.list

And put the two line into it:

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main

Then update the source and install or upgrade Ubuntu Tweak:

sudo apt-get update
sudo apt-get install ubuntu-tweak

if you have installed, just type:

sudo apt-get dist-upgrade

---

