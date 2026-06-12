---
title: "GNOME Newbie - Editing the boot menu"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by halberdier25 on 2008-01-20
Hey, I think I posted this in the right place.

I would like to be able to do one or more of the the following things with the boot menu (where you select which OS to boot), but don't quite know how to go about it:

[list][*]Remove the selection timer entirely, or put in a massively long period of time
[*]Change OS that boots after the timer expires
[*]Remove option (it shows two Vista loaders, but only one works)
[*]Reorder OSs[/list]

I understand that there are plenty of resources out there for this, but to be quite frank, it's all over my head.

Thanks in advance,

---

### Post by banewman on 2008-01-20
You can edit the file that controls most of that
type```
gksu /boot/grub/menu.lst
```
in a terminal
the options are there for time, delete entries(I would just comment them until you're sure you've got the right one), reorder entries
:)

---

### Post by CupofDice on 2008-01-20
Are you using gutsy or hardy? If you are not using them check out [GrubEd]("http://ubuntuforums.org/showthread.php?t=228104"). There is also [QGrubEditor]("http://www.linux.com/feature/123460") for KDE. I used GrubEd before Gutsy, and it worked well.

---

### Post by halberdier25 on 2008-01-20
If Gutsy = Ubuntu 7.10 (which I'm pretty sure it is), then Gutsy.

That line of code does nothing for me.  No password prompt, just asks for another command,

---

### Post by mrsudo on 2008-01-20
all you gotta do is edit your /boot/grub/menu.lst file:

```
sudo gedit /boot/grub/menu.lst
```

it shouldnt be a long file so just poke around and physically move the whole brick of text which looks like it corresponds to the boot option.  to make an option your default, replace it with the very first one.
sorry i could not be more specific.  unfortunately my /home partition is bugging up my login. 

good luck

gksu would do nothing for you because (i assume) you have a fresh install and havent yet installed the gksu app

---

### Post by Squizz on 2008-01-20
Edit your grub menu by using

```

sudo gedit /boot/grub/menu.lst

```

To change the timer - change "timout 3" to however many seconds you want it to be.

I think that by default grub will boot the OS that's at the top of the list, so just make sure that it's above your other OSs in the menu.lst file.

your vista loaders should look like;

```

title Windows Vista/Longhorn
rootnoverify (hd0,0)
savedefault
chainloader +1

```

or similar - use the hash key to comment out the lines of the one if you're unsure which doesn't boot.  Of course, you can just delete it from the menu.lst file once you're sure which one it is.

As a general guide, you can figure out which boot is which from the (hd0,0) bit.

The first number is the hard drive (0 for master, 1 for slave and so on) and the second number is for the partition (0 for the first partition, 1 for the second etc)

Hope that helps.

---

### Post by eapache on 2008-01-20
```
gksudo gedit /boot/grub/menu.list
```gksudo means run as admin (required for this file)
gedit is the text editor
/boot/grub/menu.list is the file

You can use sudo not gksudo as the other suggestions state, however you will be running a graphical application, so gksudo is much prefered. Running certain graphical apps as sudo not gksudo can break things.

---

### Post by banewman on 2008-01-20
Try ```
sudo nano /boot/grub/menu.lst
``` then
:)

---

### Post by erfahren on 2008-01-20
excellent and thorough information on GRUB and configuring the menu.lst file at: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by halberdier25 on 2008-01-20
Thank you guys all very much.  It works now.  Is the GKSU app something good to get?

---

### Post by erfahren on 2008-01-20
> **halberdier25 said:**
> Thank you guys all very much.  It works now.  Is the GKSU app something good to get?see eapache's last post

---

### Post by eapache on 2008-01-21
Sudo and su are interchangable, as are gksudo and gksu. Never quite understood why they don't just get rid of one, but they've both been there for as long as I can remember (only a few years, but things change fast around hear).

EDIT: Thanks for clearing that up aysiu. That makes a lot more sense.

---

### Post by aysiu on 2008-01-21
> **eapache said:**
> Sudo and su are interchangable, as are gksudo and gksu. Never quite understood why they don't just get rid of one, but they've both been there for as long as I can remember (only a few years, but things change fast around hear).
*gksudo* and *gksu* are interchangeable, but *sudo* and *su* are **not**!

*sudo* allows a user who is the admin group the opportunity to temporarily escalate privileges on a particular command or task--still logged in as the same user and authenticating using the same user password.

*su* allows you to switch (i.e., log in as) another user. To authenticate the switch, you need to use that new user's password. If you use *su* without specifying the user to switch to, the system assumes you want to switch to the root user. If you do this, everything you do (not just one task) will be done as root, and you will actually be logged in as root (not your own user) and will need to have root account enabled with its own password.

---

