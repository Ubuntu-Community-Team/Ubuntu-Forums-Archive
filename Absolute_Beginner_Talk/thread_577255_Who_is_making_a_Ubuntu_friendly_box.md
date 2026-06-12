---
title: "Who is making a Ubuntu friendly box?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by MaxGunnar on 2007-10-16
Getting Ubuntu to run on my old box is a bit of a challenge,  
I got it to function after some work and advice from here.

I want to be able to surf, burn DVDs  and two use two monitors as well, or at least a very wide monitor,  most my probs to date with Ubuntu have been graphics card driver issues.
Or  a new graphics card might do it for me,  I got an 8x agp slot and right now I'm using an older nvidia 5200 card.  any advice would be appreciated

---

### Post by Paulmd on 2007-10-16
> **MaxGunnar said:**
> Getting Ubuntu to run on my old box is a bit of a challenge,  
I got it to function after some work and advice from here.

I want to be able to surf, burn DVDs  and two use two monitors as well, or at least a very wide monitor,  most my probs to date with Ubuntu have been graphics card driver issues.
Or  a new graphics card might do it for me,  I got an 8x agp slot and right now I'm using an older nvidia 5200 card.  any advice would be appreciated

To answer the title of your post:

Dell is manufacturing several models with Ubuntu 7.04 (Feisty Fawn) Pre installed and pre configured.

To answer the body of your post:  Yes, video drivers in linux are a bit half-a$$ed at the moment, but are improving. Newer video cards by nvidia have drivers that were actually written by nvidia. 

The latest for the geforce fx series are here.  

[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

(My system uses a sis driver, so I can't give you firsthand info on whether this works well)

In terms of compatibility, nvidia seems to be the best for linux. They are quite proud of this :)

[http://www.nvidia.com/object/LO_20030328_6790.html](http://www.nvidia.com/object/LO_20030328_6790.html)

---

### Post by MaxGunnar on 2007-10-16
how to I put in   " sh NVIDIA-Linux-x86-100.14.19-pkg1.run  "  ?

I downloaded it and no magic happened

---

### Post by anjilslaire on 2007-10-16
Open a terminal in the directory where you downloaded it and run that command.

---

### Post by MaxGunnar on 2007-10-16
> **anjilslaire said:**
> Open a terminal in the directory where you downloaded it and run that command.

I D/L to the desktop and opened the terminal and no luck;


erika@erika-desktop:~$ sh NVIDIA-Linux-x86-100.14.19-pkg1.run
sh: Can't open NVIDIA-Linux-x86-100.14.19-pkg1.run
erika@erika-desktop:~$ sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
sh: Can't open NVIDIA-Linux-x86-100.14.19-pkg1.run
erika@erika-desktop:~$ sudo NVIDIA-Linux-x86-100.14.19-pkg1.run
sudo: NVIDIA-Linux-x86-100.14.19-pkg1.run: command not found
erika@erika-desktop:~$ 


Total NOOB here but I really want to dump microsquish.

---

### Post by Pumalite on 2007-10-16
Ctrl+Alt+F2
login with username
your password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIAxxxxxx.run
sudo /etc/init.d/gdm start
If need be: startx
(make sure you have build-essential installed:
At the Terminal: sudo apt-get install build-essential)
(before you attempt to compile your driver into the kernel)

---

### Post by MaxGunnar on 2007-10-16
attempted that and it wouldn't take:confused:

the good news is I didn't break it like I've done before,  I guess I'll have to wait for the experienced people to put it in a pretty package for us casual users.  I suppose I can limp along with just one monitor...............   Thanks for the help I did learn something

---

### Post by barkej on 2007-10-16
You might find the [Envy]("http://albertomilone.com/nvidia_scripts1.html") script more to your liking. Same Nvidia driver but more automated setup.

---

### Post by bodhi.zazen on 2007-10-16
> **Pumalite said:**
> Ctrl+Alt+F2
login with username
your password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIAxxxxxx.run
sudo /etc/init.d/gdm start
If need be: startx
(make sure you have build-essential installed:
At the Terminal: sudo apt-get install build-essential)
(before you attempt to compile your driver into the kernel)

> **MaxGunnar said:**
> attempted that and it wouldn't take:confused:

the good news is I didn't break it like I've done before,  I guess I'll have to wait for the experienced people to put it in a pretty package for us casual users.  I suppose I can limp along with just one monitor...............   Thanks for the help I did learn something

From a terminal (Ctrl-Alt-F1 or F2), log in if needed.

```
sudo -i

# enter password

/etc/init.d/gdm stop

apt-get install build-essential linux-headers-`uname -r`

#  Note those are bac tics ` (by the number 1) and not single quote '

sh NVIDIA*

exit

sudo /etc/init.d/gdm start
```

Log in, open a terminal,

```
gksu nvidia-settings
```

---

### Post by Paulmd on 2007-10-16
> **MaxGunnar said:**
> I D/L to the desktop and opened the terminal and no luck;


erika@erika-desktop:~$ sh NVIDIA-Linux-x86-100.14.19-pkg1.run
sh: Can't open NVIDIA-Linux-x86-100.14.19-pkg1.run
erika@erika-desktop:~$ sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
sh: Can't open NVIDIA-Linux-x86-100.14.19-pkg1.run
erika@erika-desktop:~$ sudo NVIDIA-Linux-x86-100.14.19-pkg1.run
sudo: NVIDIA-Linux-x86-100.14.19-pkg1.run: command not found
erika@erika-desktop:~$ 


Total NOOB here but I really want to dump microsquish.

I think perhaps you downloaded a corrupt archive, as I get:

```
paul@paul-desktop:~$ sh NVIDIA-Linux-x86-100.14.19-pkg1.run 
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 100.14.19

```

At this point I hit ctrl C to prevent the nvidia driver from actually installing in my SiS system. 

Try re-downloading the file. It should be 14.5 MB.

[COLOR="Red"]EDIT:Wait a minute: You downloaded it to the DESKTOP, but your code shows your working directory is the HOME Directory.

Before you redownload that archive, type 

```
cd Desktop
sh NVIDIA-Linux-x86-100.14.19-pkg1.run

```
[/COLOR]

---

### Post by russell.h on 2007-10-16
He put it on his desktop, but was executing it from his home folder.

When you open a terminal start by typing "cd Desktop" to switch the terminal to your desktop before executing that command (sh whatever).

---

### Post by MaxGunnar on 2007-10-17
> **bodhi.zazen said:**
> From a terminal (Ctrl-Alt-F1 or F2), log in if needed.

```
sudo -i

# enter password

/etc/init.d/gdm stop

apt-get install build-essential linux-headers-`uname -r`

#  Note those are bac tics ` (by the number 1) and not single quote '

sh NVIDIA*

exit

sudo /etc/init.d/gdm start
```

Log in, open a terminal,

```
gksu nvidia-settings
```


WHHOOOOO HHHHOOOOOO  Its working now,  got both monitors and rebooted just to make sure it stuck.  it did, thanks guys,     But you will forgive me if I still have another HD with XP laying around just in case won't you      ;)

---

### Post by avik on 2007-10-17
> **MaxGunnar said:**
> WHHOOOOO HHHHOOOOOO  Its working now,  got both monitors and rebooted just to make sure it stuck.  it did, thanks guys,     But you will forgive me if I still have another HD with XP laying around just in case won't you      ;)

You'll see.  The next thing you know, you'll find the XP partition just lying there, worthless.  ;)

---

### Post by Paulmd on 2007-10-17
> **MaxGunnar said:**
> WHHOOOOO HHHHOOOOOO  Its working now,  got both monitors and rebooted just to make sure it stuck.  it did, thanks guys,     But you will forgive me if I still have another HD with XP laying around just in case won't you      ;)

I use XP, on my other computer (I actually like XP, just not WGA and associated "technologies"). *Many* Linux users have a dual boot setup. You are forgiven.

---

### Post by corowakid on 2007-10-17
For all things nVidia and Ubuntu, have a look here:

[www.albertomilone.com](www.albertomilone.com)

follow the instructions, and print out anything you think you might need. Its the best guide I've come across, and let me install a 22" screen with a GT7300 and get 1680x1050. Really works!

---

### Post by Sef on 2007-10-17
> Who is making a Ubuntu friendly box?

[System76]("Http://system76.com") makes them well and the support seems really good.

---

### Post by MaxGunnar on 2007-10-17
> **avik said:**
> You'll see.  The next thing you know, you'll find the XP partition just lying there, worthless.  ;)

What I liked about Ubuntu was the fact I could insert the 7.10 CD click on install, go get a cup of coffee and a donut and by the time I got back my PC was ready to go to work.   Of course you can't beat the price.   Installing the "toys" however took a bit of re training.  If I was going to start a small business that required a few PCs  I'd go with Ubuntu.  As it stands now I have only one app that requires XP.   Oh in case anybody is wondering,  Vista suxs

---

