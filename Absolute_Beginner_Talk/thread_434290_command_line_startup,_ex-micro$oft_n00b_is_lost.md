---
title: "command line startup, ex-micro$oft n00b is lost"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by FlyingPenguin542 on 2007-05-05
I'm a Windows convert (aka used to GUI and a complete linux n00b) so i have absolutely NO IDEA what to do in this situation:

I believe i inadvertently removed something that i definitely shouldn't have X_x. Basically, I installed a package that MAJORLY conflicted with another, got a broken package OMG alert, so i deleted the messed-up  one that showed in Synaptic's "broken" filter... however, said deleted package was apparently essential for Gnome to work. 

Now  I've got a laptop in text-only command line mode, and internet wasnt recognized when the desktop DID work- not even when connected via LAN cable (my original idea was to apt-get gnome somehow). i know next-to-nothing as far as code goes- just random apt-get and dpkg commands. 

I WOULD just reinstall again using the live-cd, but I have to move my music+documents first. I tried running Ubuntu from teh CD drive, mounted my internal drive by accident, and thought I could just drag-n-drop my stuff into my external. BUT...

 Enter problem #2- files are locked, and when i try to right-click and set the permissions properly, it just says i haven't got the permission cuz I'm not the owner.

Any help would be much appreciated! It's probably an obvious "duh" solution, but I'd rather feel like an idiot than have a messed-up laptop (or worse, try and fix it by myself and have a DEAD laptop)

---

### Post by gradedcheese on 2007-05-05
so you can boot to a shell?  what package did you add/remove/delete?  Perhaps see if apt tells you anything:

```

sudo apt-get update
sudo apt-get upgrade

```

As for the files, you can change their owner:

```

sudo chown user_name_here file_name_here

```

or for a directory:

```

sudo chown -R user_name_here file_name_here

```

You don't need to reinstall the OS, anything you did can be fixed.

---

### Post by rickycodie on 2007-05-05
here try this it might help.

[http://ubuntuforums.org/showthread.php?t=410400&highlight=restoring+x](http://ubuntuforums.org/showthread.php?t=410400&highlight=restoring+x)

---

### Post by FlyingPenguin542 on 2007-05-05
lets see.... apt-get update shows a giant list of things its trying to get to but can't resolve archive us.archive.ubuntu.com

apt-get upgrade talks about bcm43xx-fwcutter (fails, can't connect to something it needs to (subprocess post-installation script returned error exit status 6) but i KNOW it wasn't that package that messed me up.

I was just thinking, could i snipe the necessary desktop stuff from the live disk if i inserted it? and if so, how could i set things to have apt-get look there?

*goes to read suggested thread*

---

### Post by gradedcheese on 2007-05-05
Ok, I am trying to piece together what happened here, let me know if this is right:
1) you are unfortunate enough to have Broadcom wireless
2) you used firmware cutter / ndiswrapper to install a windows driver for it
3) it used to work, but now it doesn't and you can't get online
4) so apt-get doesn't work

Yes, you can add the Ubuntu CD to your /etc/apt/sources.list file in order to pull packages from there.  However you probably want to find out what's broken or missing first.  You don't recall what it was that you removed?

---

### Post by FlyingPenguin542 on 2007-05-05
Yep, sounds about right.

relevant laptop stats: HP zv6130us w/  broadcom 802.11 b/g wireless card

and i definitely wasn't thinking, i didnt write it down/record it at all. which was, of course, stupid.

the scrolling list of things that getting uninstalled (for me, the "...oh #*% i shouldnta done that" moment) , however, included nautilus, a bunch of things related to gnome....

Is there some sort of list of recent installs i can access?

*****oh, and from the thread rickycodie linked me to... 

root@linux-laptop:/etc/X11# ls

gets me something that looks like

X__________________ Xsession.d____________app-default____________ fonts__________xkb
Xresources_________Xsession.options__________cursors______________rgb.txt_______xorg.conf
Xsession__________Xwrapper.config_______default-display-manager______xinit__________xserver

and when i enter: sudo /etc/init.d/gdm restart
i get... nothing. oh dear >.< but of course i could be doing it wrong...

---

### Post by gradedcheese on 2007-05-05
Ok, this shouldn't be too hard to fix.  Add the CD to your sources.list and then apt-get install the "ubuntu-desktop" meta-package, which (I think) will cause apt to grab all the Gnome desktop stuff, including Nautilus.  I think you just put the CD in and then run (as root or with sudo)

```

apt-cdrom add

```

---

### Post by FlyingPenguin542 on 2007-05-05
gah. entered code, CD is all verified and checks out, wrote new sources list... then when i try and get ubuntu-desktop, it's still MIA. Lessee... it says it can see 2 package indexes.

Source list entries for this disc are:
deb cdrom: [Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

---

### Post by gradedcheese on 2007-05-05
You need to:

```

sudo apt-get update

```

after adding the CD, sorry I forgot to mention that.

---

### Post by FlyingPenguin542 on 2007-05-05
Tried those in order, still tries to get updates online I have the feeling i'm missing something thats right under my nose....

OH i just noticed when it says its updated the lists, it says that it sees 2 but only lists the Restricted list as actually added. weird.

*** cd command --> cdrom drive... nothin. 'course i dunno if it woulda done anything, but hey. worth a try.

edit x2: uninstalled bcm43xx-fwcutter for good measure, cuz it was just sitting there in limbo being useless anyways.

---

### Post by FlyingPenguin542 on 2007-05-05
*various swearing* Only option I see is booting from CD and trying to reset permissions :(

---

### Post by FlyingPenguin542 on 2007-05-06
Alright, to make this post useful in the end to somebody- here's how I managed to copy my files onto an external drive when not the "owner":

Booted up through the Live CD.

Mounted my internal drive (it just showed up as an unknown storage thing  til i clicked on it, and Ubuntu mounted it automatically for me)

Made a launcher (right-click on teh desktop), and in the command box I put:

> gksudo "gnome-open %u"

I drag-and-dropped the folder I needed full access to (in this case, "Music") onto the launcher I'd created

Thus, it opened- but in SUPER-EXTRA-SPECIAL window, where I had owners privileges- thus, could reset all permissions I needed.

Then I moved whatever files I damn well pleased into the other drive. Not gonna lie, I did a mad crazy happy dance... but I mean, come on, who WOULDN'T? All my Killswitch Engage/Bullet For My Valentine/Children of Bodom/Rise Against/Soilwork/[insert artist here] were safe. 

yay for this page: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by gradedcheese on 2007-05-06
but I showed you how to change the owner?

---

