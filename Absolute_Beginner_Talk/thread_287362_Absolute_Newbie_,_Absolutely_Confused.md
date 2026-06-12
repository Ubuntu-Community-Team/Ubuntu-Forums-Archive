---
title: "Absolute Newbie , Absolutely Confused"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by damionh on 2006-10-28
Hi there

Firstly let me congratulate whoever for creating this wonderful Operating System (doesnt that show how new i am) 

Having used Dos, Win 3.1, 3.11, 95, 98 , Xp etc etc i finally saw the reason for trying out a linux distro. The price of Vista !! Now it has i just cant believe how good this thing is ! 

However, i am a little confused. Actually, massively confused. 

Im trying to install a driver for my graphics card. 

I am using a dualboot (ok still holding onto the xp , hey i paid for it) between Ubuntu 6.06 and Xp Pro. My graphics when i look for a resolution under System-Preferences-Screen Resolution can only go up to 1024x768 but im sure i can get better. Im using a belinea 21" monitor which in win ive managed to get about 2048xwhatever out of, so im sure linux can do better.

so far i have downloaded NVIDIA-Linux-x86-1.08776-pkg1.run  but im unsure what i am to do with it? there seems to be a lot of jargon (as usual surrounding os's) which i dont understand and am looking for a laymans guide on how i get the driver into the system.

i have an athlon xp 2800+, my graphics card is a XFX Geforce 6600GT 128mb DDR3 with Dual DVI and TV. i have 1.5 gb ram, my linux swap file is 1gb (though im probably getting a little ahead of myself here) 

Can anyone help by pointing me in the right direction please ?

by the way, did i say that this thing is fantastic ? all i need is a good game and im away !

---

### Post by Bachstelze on 2006-10-28
Hi and welcome to Ubuntu :)

To install nvidia drivers :

```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

and that's all :)

---

### Post by damionh on 2006-10-28
What a quick reply, many thanks !!!!

Im almost there .. i got an error message ..

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

so i ran the command ...

md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum

in the terminal window

and i got ..

Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

do you know how i can do this ? (restart "x" that is) 

sorry to be a pain ... many thanks for the advice !

---

### Post by GStubbs43 on 2006-10-28
Except, if you haven't already put in sudo apt-get install nvidia-glx, use ```
 sudo aptitude install nvidia-glx
``` Aptitude is better at managing dependencies. :)

EDIT: Restart x with ctrl+alt+backspace

---

### Post by damionh on 2006-10-28
erm, oops, looks like i killed something, i did the ctrl+alt+backspace and i got a message something like "cannot restart your x-server" then loads of text from which i did take the lines ..

WW Nvidia No MAtching Device Section for instance  (BUSID PCI:1:0:0) found 

my card is an agp, does that matter ? 

and also

EE No devices detected 
fatal server error 
no screens found

is there a chance of me getting ubuntu back ? or should I reinstall ? 

There was also a lot of text on another page , not sure what that was though...

help again ? please....

---

### Post by catlett on 2006-10-28
Everything is fine. You need to restart X like the previouis poster said. The problem is the previous poster didn't tell you how to do it.
After you do ctrl-alt-backspace, enter this command at the text command line
```
startx
```That will restart the x server.
This may be of some help to you. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) Just follow it from the beginning because you have to change a document on your system that deals with repositories that hold software. Other than that, you can pick and choose what you want to install from the list. To install from the guide, just copy and paste the commands into your terminal.

P.S. If the startx doesn't work for some reason, enter this command sudo ```
dpkg-reconfigure xserver-xorg
``` Then just follow the prompts. This reconfidure the x server.

---

### Post by damionh on 2006-10-29
Now ive gone from Confused to downright baffled. I did the ...

dpfg-reconfigure xserver-xorg

thing, and did startx but the screen went black and there seems to be no input as the green light on the monitor turns amber (ie no signal being received) 

Ive already downloaded 6.10 and i am a complete newbie, if i need to reinstall would i be best just reinstalling 6.10 instead of trying to get this version back (ie is it corrupt? )

lastly , if i put on 6.10 would my graphics card driver be installed automatically ? or would i have to do the 

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

thing (possibly replacing apt with aptitude as the second poster mentioned)

I think if i had been running windows i would have already reinstalled by now but for the help received here, i havent.

Many thanks in advance.

---

### Post by Bachstelze on 2006-10-29
The first message you got when running nvidia-glx-config suggests that you already did some tinkering with your xorg.conf (previous attempt to install the drivers, most likely) and for some reason that confused the driver. The safe bet is to reinstall so you have a fresh xorg.conf and then install the drivers the way I told you above.

---

### Post by damionh on 2006-10-29
Will do , many thanks for the time and help received from yourself and the other posters.

---

### Post by damionh on 2006-10-29
Hi there, now back again. 

Ive now installed 6.10 and am looking to increase the desktop resolution available again, i think i have to (again) attempt to get the nvidia driver for the graphics card shown below onto the system (its an agp, this may have been a problem before ??? )

Do i still type ...

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

even though ive changed the version from 6.06.1 to 6.10 ?

do i do anything else ? or just that from inside terminal window ..

This is an absolutely fresh install of 6.10, i have done nothing else except log in..

=======================

One last question, why is it that with Windows i begrudge paying so much yet with this im donating money freely !! i think that says it all about this os and its community !

---

### Post by Kulgan on 2006-10-29
the commands should still be the same.

> One last question, why is it that with Windows i begrudge paying so much yet with this im donating money freely !! i think that says it all about this os and its community !

two answers possible:
1. Windows sucks. Ubuntu doesn't.
2. Ubuntu is addicting. As is all linux :D

---

### Post by NeoLithium on 2006-10-29
> **Kulgan said:**
> two answers possible:
1. Windows sucks. Ubuntu doesn't.
2. Ubuntu is addicting. As is all linux :D

Definately, I haven't been able to think about anything but linux since I switched :)  My MS disks are all now lovely coasters that I use...

---

### Post by raqball on 2006-10-29
I don't miss windoze one bit and have never thought about looking back since my change!

I think everyone should donate to ubuntu (or their distro of choice). Even a few bucks helps :)

---

### Post by MasterOfDisaster on 2006-10-29
Pretty much.  Installing your graphics driver the first time is hard, but after that, its pretty simple.

Thats the gist of it, but you want to do a uname -r in the terminal, (mine comes out as 2.6.17-10-generic), and type:
*sudo apt-get install linux-generic*

Then
*sudo apt-get install nvidia-glx*

Then finally,
*sudo nvidia-xconfig*

If this gives you the error you encountered before, type in
*sudo gedit /etc/X11/xorg.conf*

and replace 'nv' with 'nvidia' under the 'Device' section.

Then press Control-Alt-Backspace to restart the server.

It should be installed then.

---

### Post by Kulgan on 2006-10-29
isn't this kind of stuff more for the testimonial section? Or perhaps the windows bashing forum O.o

damionh, how's it going?

---

### Post by kinematic on 2006-10-29
i would just install the driver from the nvidia site
first get the buil-essential package
> aptitude install build-essential(also look in synaptic if the kernel headers are installed,look under linux-headers
download the latest beta driver(it says beta but it's stable)or the latest stable one and put it in your /home directory.
then go to the shell with ctrl>alt>f1 and do
> sudo killall gdm or sudo init 3(kills the x-server and anything gui related)
then do 
> cd /home/yourusernameand 
> sh NVIDIA......pkg1.run(if you press the tab button after the first few letters the shell will autocomplete it
and let it update your xorg.conf.

---

