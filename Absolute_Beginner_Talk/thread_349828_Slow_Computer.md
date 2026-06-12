---
title: "Slow Computer"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by dethredic on 2007-01-30
I got an old computer from a friend who said it didn't work.
Just had to replace the CMOS battery and bam its up and running.

Anyways this thing has 128 mb ram, P2 and i am finding the performance pretty sluggish.

Took 2 mins for openoffice to open.
go over a menu takes 3 seconds before the pictures show up ect.

Is there anyway to make Ubuntu run faster.

I am willing to sacrifice appearance.

---

### Post by meng on 2007-01-30
Try Xubuntu (XFCE rather than GNOME) and perhaps use Abiword and Gnumeric rather than OpenOffice, if your needs are simple. If you want lightning fast performance, consider fluxbox (Fluxbuntu or Damn Small Linux are options).

---

### Post by IYY on 2007-01-30
On 128 MB, switching to XFCE would make a *huge* difference. Switching to IceWM or Fluxbox would be an even bigger difference. Then, make sure that you are using the lighter GTK themes (the Ubuntu theme is one of the heaviest ; Clearlooks might be a big lighter, but the XFCE, Mist and Redmond themes are surely much lighter). 

Then, use the lighter applications. XMMS for music, AbiWord for word processing, xterm or aterm as the terminal... Firefox is ok as a web browser, but opera can be a bit faster, and Dillo is insanely fast but will not render all pages correctly (and of course, no flash and AJAX).

---

### Post by homh on 2007-01-30
I put Damn Small Linux on a PII laptop with 192 ram and ran it off the CD and it was fast.
Get rid of some of those memory hogs with the standard UBUNTU installation and you should do find and have all the functions and applications you need.  ABIWORD is actually my favorite word processsor.  You need to go with lightweight applications whenever possible and get rid of GNOME.

---

### Post by dethredic on 2007-01-30
Sorry but i am new to linux so please forgive my n00bness.

> switching to XFCE would make a huge difference
do i do this in ubuntu? or is it another OS i have to install.

> 
Switching to IceWM or Fluxbox would be an even bigger difference
From what i read i don't install these, i just put in the CD and go then when im done take out the CD and put it back in when i want to use it again. Is that right?

---

### Post by 3rdalbum on 2007-01-30
XFCE is just a desktop environment. You can install it with this command:

```
sudo apt-get install xfce4 xfce4-utils
```

Log out, at the login screen choose "Options" and "Sessions...". Enable XFCE 4. Log in, and you'll be in XFCE. You'll probably also want to think about getting rid of OpenOffice.org and some of the other bigger programs, and finding smaller replacements for them (Abiword and Gnumeric, for instance).

---

### Post by IYY on 2007-01-30
> 
do i do this in ubuntu? or is it another OS i have to install.

If you don't have Ubuntu installed yet, you could just grab the Xubuntu CD and install that. It's just Ubuntu with XFCE and a lighter selection of apps. However, if you already have Ubuntu installed, you can add XFCE with the command:
```

sudo aptitude install xubuntu-desktop

```


> From what i read i don't install these, i just put in the CD and go then when im done take out the CD and put it back in when i want to use it again. Is that right?

No; IceWM and Fluxbox are small desktop environments (though really, when they are so minimal they tend to just be called window managers) which can be installed on any Unix-like operating system with X11. To get Fluxbox in Ubuntu:

```
sudo apt-get install fluxbox
```

and to get IceWM:

```
sudo apt-get install icewm
```

you will be able to select which you want to run in the login screen. Note that you can have XFCE, Gnome, IceWM and Fluxbox all installed on the same machine, allowing you to select whichever you feel like using.

Also note that IceWM and Fluxbox tend to look quite shabby by default, but are easy to transform into decent-looking systems:

[http://yakubovich.blogspot.com/2006/11/use-icewm.html](http://yakubovich.blogspot.com/2006/11/use-icewm.html)

Sorry to be pimping my own blog, but I think it gives a very short introduction to just what IceWM, what it looks like and what it's good for.

---

### Post by Motoxrdude on 2007-01-30
Yes, xfce and fluxbox are the only way to go with computers that have 128MB or less of ram. That and poor graphic accelerators.

---

### Post by dethredic on 2007-02-06
> sudo aptitude install xubuntu-desktop

error
couldn't any package with whose name or description matched "xubuntu-desktop"

> 
sudo apt-get install xfce4 xfce4-utils
error
E: couldn't find package xface4


help please?

---

### Post by chick penguin on 2007-02-07
[QUOTE=IYY;2085759]If you don't have Ubuntu installed yet, you could just grab the Xubuntu CD and install that. It's just Ubuntu with XFCE and a lighter selection of apps. However, if you already have Ubuntu installed, you can add XFCE with the command:
```

sudo aptitude install xubuntu-desktop

```

.... To get Fluxbox in Ubuntu:

```
sudo apt-get install fluxbox
```

and to get IceWM:

```
sudo apt-get install icewm
```

I followed the instructions and installed all three of these and am now test driving this on my old machine that I have set up for this experiment. Fun. I was glad to have all my links and bookmarks and all else still inplace, as I installed xubuntu as per instructions and thought I wiped out Dapper and the files. But it is all there. 
What would have been the difference if i had installed 
 sudo apt-get install xfce4 xfce4-utils
instead of the whole desktop environment?

Looking forward to exploring these three to find out which works best on this machine.

Thanks to all. 
Who knows I might get sound out of this machine yet.

---

### Post by lyceum on 2007-02-07
> **dethredic said:**
> error
couldn't any package with whose name or description matched "xubuntu-desktop"


error
E: couldn't find package xface4


help please?

Are you connected to the net?

---

### Post by dethredic on 2007-02-07
No i am not connected.

I cant get that working - [http://ubuntuforums.org/showthread.php?p=2081127#post2081127](http://ubuntuforums.org/showthread.php?p=2081127#post2081127)

---

### Post by lyceum on 2007-02-07
sudo apt-get only works if you are on line. If you want Xubuntu you will need to download it and burn a disk. Shipit doesn't send them. Sorry...

---

### Post by dethredic on 2007-02-07
can you help me get online?

---

### Post by lyceum on 2007-02-08
> **dethredic said:**
> can you help me get online?

I can't, that is not one of my strong points, but by posting I will bump this thread so someone else can see it. That may help, but you may want to bump the tread with your question on it. I looked at it and it is out of my league. Either your hard ware is not compatable or using Ubuntu on such an old PC is hindering things, but I do not see how that would happen.

-edit-
What ethernet card are you using? Are you sure the card works? Do you have the abilaty to swap cards or add another card/means to assess the net in any way other than USB port? (I have had no luck connecting to the net through USB)

With this info I will see what I can figure out. I looked at your other thread again. I still have no idea what it is talking about. I am a hardware guy (sorry!)

---

### Post by dethredic on 2007-02-08
Thanks for trying to help

Before i had windows 2000 on it and i plugged in the eathernet cord and it worked i didn't have to set anything up or anything.

thanks why i now confused

---

### Post by lyceum on 2007-02-08
If it is a PC, not a laptop, you should be able to get a used card from a used PC store for about $5 that would work. I would say that is your best bet.

---

### Post by dethredic on 2007-02-08
Its a laptop

---

### Post by dethredic on 2007-02-10
I guess you don't feel like helping me anymore :(

---

### Post by lyceum on 2007-02-10
No, I am just out of ideas. Sorry. If you can get a card that works with Linux and get on line that is great, but I do not know enough to help you get a card that does not work with Linux working. 

By the way, can you post what kind of card you have? I can try to look something up, like a how to, if I know what kind. I have a Broadcom 4311 WiFI card, and I can't get it working so I would be the blind leading the blind. Sorry! :(

---

### Post by Unlockitall on 2007-02-10
im running an even slower pc then the one he mentioned, where could i get a copy of damn small linux?

---

### Post by kerry_s on 2007-02-10
-> [ftp://gd.tuwien.ac.at/opsys/linux/damnsmall/current/dsl-3.2.iso](ftp://gd.tuwien.ac.at/opsys/linux/damnsmall/current/dsl-3.2.iso)

If you want to look around at distros-> [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Unlockitall on 2007-02-10
thank ypu for the link, i will wait until i get to school to download it, i have dial-up, the school has T1

---

