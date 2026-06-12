---
title: "linksys wirelesas card"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by fjkey on 2007-06-28
I've posted before and canot even find the help that was suggested.
I did how ever saved the link to read doc. I went step by step to down load ndiswraper to ubuntu.
However I cannot seam to install it? I was going to put driver in of win xp because it works on other
half of boot drive.On the dvd virsion of ubuntu that I installed there is allready a virsion of ndiswrapper,
But when I try to aply,it pops up please install cd draper drake? so I'm at an inpass unless the book
I'm reading helps quickly.LOL If you have a short cut in the copy of my book(Ubuntu unleashed).
Or Can step by step me through the install of ndiswrapper in hope of surfing the web on ubuntu.
I can tinker from there? I'm question my sanitiy?? I'm very new, I've watched of the versions ms evolve.
I would like to permently depart from win. Have pitty on this old dude!!
Thanks in advance!

---

### Post by Atreus12 on 2007-06-28
Are you having trouble installing ndiswrapper or installing the wireless drivers?

To install ndiswrapper, open your terminal
applications->accessories->terminal

copy and paste this line in (you can just highlight it, and then middle click to paste)
```

sudo aptitude install ndiswrapper

```

If you do not have a working internet connection, it should prompt you to insert the CD, and it will install ndiswrapper from the cd.

Once you get ndiswrapper installed, you need to get a copy of the win XP drivers for your wireless card. Once you get them, go back to the terminal

$ sudo ndiswrapper -i ~/drivers/drivername.inf

where you replace ~/drivers.... with the path to your driver (the one that ends in .inf)

at this point, check to see if it worked

```
 sudo ndiswrapper -l 
```

It should list the driver you just installed.

Provided that worked, run the following commands one at a time.

```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -m
```

At this point you may need to restart. If everything worked, you can configure your network with 'network manager'.

If you are configuring a network with WPA, see this [link.](http://ubuntuforums.org/showthread.php?t=202834)

If something doesn't work right, see this [link.](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


Just out of curiosity, what linksys wireless card do you have? I have the WUSB54Gv1, which only runs with ndiswrapper. The more common card is the WUSB54Gv4, which I believe runs natively and doesn't require ndiswrapper.

-Andrew

---

### Post by fjkey on 2007-06-28
I have 0000:02:04.0
network controller:broadcom corporation
BCM4303 80311b
wireless L
AN controller(rev 02)
I'm reinstalling ubuntu on single hd. Laptop is my internet con.
I'm having trouble installing ndiswrapper in os. I will save this page and follow instructions shortly!
thank you for all of your help!

---

### Post by fjkey on 2007-06-29
It will not let me extract from cd. The cd is sony cd-rw. I have tried and unziped and still nothing.
I tried have  ad and remove pro,said that I didn't have right permission to extract archives in the folder "/media/cdromo" Am I going wrong direction?

---

### Post by kakalaky on 2007-06-29
that is the actual disk and is read only, that's why you can't extract there.  copy the file(s) to somewhere under your home dir and then extract.

---

### Post by fjkey on 2007-06-29
I have win xp folder on the desktop. will not let me install. says ndiswrapper-modules-1.8 is in a paket.
says need to get ob of achives.After upacking ob will be used? How many places in ubtu uses dos like comands. the terminal & or ? I need to find a list, some how install winxp driver,or ndiswrapper.
I don't think it was installed.but I have a winxp file on desktop,nothing seems to be in it?

---

### Post by fjkey on 2007-06-29
I have niswrapper-1.47.tar.gz on desktop please help to install!!
I'm still searching book and thread.Been to help doc. severl times now.

---

### Post by dagrump on 2007-06-29
1st what type of laptop? You could just need to enter some info, look into system>admin>network. I think my laptop uses that same chip & I didn't need to load anything extra.

---

### Post by fjkey on 2007-06-30
I don't have a laptop,I have a desktop.

---

### Post by Atreus12 on 2007-06-30
Does the desktop have any internet connection?

If you are still having trouble installing ndiswrapper, try the following

Go to system->administration->synaptic package manager

from the menu at the top, choose settings-> repositories

**(I think it is called 'settings', I don't have gnome installed, so I'm just going from memory, but what you want is to choose 'repositories')

Now browse through your options in this list, and what you want to do is find the button "add cdrom to repository list" (or something similar)

Now go back to the terminal and run 

```
sudo aptitude update
```
```
sudo aptitude install ndiswrapper
```

If that doesn't work, then post the output of 

```
aptitude search ndiswrapper
```

and copy and past the contents of 

```
gedit /etc/apt/sources.list
```


To answer your question about the 'terminal commands', 
yes ubuntu uses them. No you really don't 'need' to learn them. Basically, most things in the terminal have a graphical equivalent.

The difference is, it's easier to type out a code, and have you copy and paste it in the terminal, than it is to visually describe the sequence of steps needed to go through a graphical program.

Ad/remove programs is basically the same thing as aptitude. One is graphical, the other is a text based program.

-Andrew

PS: You may want to browse through the supported network cards:
[Link](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by fjkey on 2007-06-30
Atereus12 First of thank you for your help! Some how things are just not working.
I have a conection for the internet on our laptop.Ubuntu is on mydesktop.
I went to synaptic pakage manager,add cdrom- I get (Err scaning the cd  E:faild to mount the cdrom)
Another window pops up and says You have inserted a blank disk what would you like to do?
From terminal window I get   err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
temporary failure resolving 'us.archive.ubuntu.com' & one security err message.
My netwok card is linksys--- 0000:02:04.0 netwok controller:Broadcom Coporation
BCM4303 802.11b   wireless L an Controller(rev 02)
What do you think?

---

### Post by Atreus12 on 2007-06-30
[quote=doc.gwos.org]

Adding a CD-ROM or DVD repository

Insert the CD or DVD and in the terminal write:

```
sudo apt-cdrom add
```
[/quote]

If that works (e.g. doesn't give you an error), then go back up to my first post and go from there.

If that doesn't work, then I'm out of ideas, and probably a little out of my depth, as I'm a fairly new user as well. At this point you have two options. 

A) Lug your desktop over near you router and plug it in via ethernet cord, and then follow my first post. (that's what I did on my very first install when I didn't know what I was doing ;) )

B) Post a new thread in the beginner forum asking for help on installing packages from the cd. To get the most help, the title should be something like: "Unable to add cdrom as repository." and then explain that you don't have an internet connection, and you want to be able to install packages from the cd.

The reason for posting a new thread is that 0 reply topics seem to get answered first.

In any case, post back here and let me know what happens. I wish my knowledge was a little more extensive....because I don't think this is a difficult problem, I just don't know how to fix it.

---

### Post by fjkey on 2007-06-30
I tried to install cdom comand,did not work thanks.
I play music and downloaded data to the desktop from the cdrom.I don't understand err mesage.
I greatfull for your help! Thank you!
fjkey

---

