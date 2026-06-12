---
title: "Should I install Dapper?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by hoarythehedgehog2009 on 2006-04-13
I am completely new to linux, and am currently edging towards installing kubuntu breezy, but wonder if I should install Dapper instead:
Does dapper support the package manager yet?
Is it user friendly?

---

### Post by truNWA on 2006-04-13
Well since Dapper is in the DEvelopment stages and you're new, i would suggest Breezy. Plus, Dapper also crashes from time to time (again Development).

---

### Post by taurus on 2006-04-13
Since you are new to Ubuntu, I highly recommand you stay with Breezy because it's stable and you don't have to worry about bugs or crashes.  Wait until after June 1st when Dapper Drake comes out, then either upgrade to Dapper or install Dapper on your machine.

---

### Post by dermotti on 2006-04-13
I don't see a problem going with dapper. If anything, it will be easier to use. 

With dapper you could run into bugs, but i can say from experience, i havnt seen any and i installed it 2 months ago.

---

### Post by hoarythehedgehog2009 on 2006-04-13
okay, thanks I might install xubuntu breezy, it is supported in the forums?

---

### Post by taurus on 2006-04-13
[QUOTE=hoarythehedgehog2009]okay, thanks I might install xubuntu breezy, it is supported in the forums?[/QUOTE]
Everything related to Ubuntu (and some not so related) is supported here.  ;)

---

### Post by dermotti on 2006-04-13
Only downside to Breezy Xubuntu is you only get version 4.2.3 of XFCE

XFCE 4.3, which comes with Dapper, is much much better.

---

### Post by truNWA on 2006-04-13
If you really want Xfce, I would go with Dapper, even if you are new

---

### Post by hoarythehedgehog2009 on 2006-04-13
is the package manager supported by dapper? Is the a chance Dapper will mess up my window's partition? Do gnome and kde apps work in Xubuntu?

---

### Post by hoarythehedgehog2009 on 2006-04-13
Bump

---

### Post by dermotti on 2006-04-13
Yes
Its just as likely with Breezy
Yes

---

### Post by Sutekh on 2006-04-13
[QUOTE=hoarythehedgehog2009]is the package manager supported by dapper?[/quote]Of course, Synaptic is part of Ubuntu, whether it be previous releases or Dapper, GNOME/KDE/XFCE or whatever you use Synaptic will work.


[quote=hoarythehedgehog2009]Is the a chance Dapper will mess up my window's partition?[/quote]Only unless you tell it to.  

[quote=haorythehedgehog2009]Do gnome and kde apps work in Xubuntu?[/QUOTE]There is no such thing as a GNOME app or a KDE app.  Currently I don't use GNOME/KDE or XFCE at all.  Just a simple window manager OpenBox.  But I still can use Syanptic, GNOMEBaker, Amarok, whatever I like.

If you install an application using Synaptic, all the necessary packages to run it will be installed as well.

---

### Post by 3rdalbum on 2006-04-14
Agreed with the above poster. You can run any program on Xubuntu, but with some programs it also has to install pieces of GNOME or KDE. If you're running Xubuntu, it's likely that you have an older computer... so you probably wouldn't want to run GNOME-dependant apps as they will use up a fair bit of memory and run slowly.

---

### Post by aysiu on 2006-04-14
[QUOTE=Sutekh]
There is no such thing as a GNOME app or a KDE app.[/QUOTE] KMail isn't a KDE application? Evolution isn't a Gnome app? I'm not sure I agree with you there.

Of course, Gnome applications and KDE applications work in any environment--KDE, Gnome, XFCE, IceWM, Fluxbox, etc.

---

### Post by Sutekh on 2006-04-14
[QUOTE=aysiu]KMail isn't a KDE application? Evolution isn't a Gnome app? I'm not sure I agree with you there.[/quote]I didn't mean it in the way you are suggesting.  I agree that applications are made for a particular environment, but not that they can't work outside that environment.
[QUOTE=aysiu]
Of course, Gnome applications and KDE applications work in any environment--KDE, Gnome, XFCE, IceWM, Fluxbox, etc.[/QUOTE]
I meant it pretty much like this.  

I can run Evolution without a full GNOME environment, KMail without a full KDE environment, etc.   I thought that the poster was asking if a package like Evolution (for arguement's sake) could be run without using GNOME.

---

### Post by aysiu on 2006-04-14
It's cool, Sutekh. I think we get each other.

---

### Post by Sutekh on 2006-04-14
I have a habit of assuming that people are communicating on the same level as me.  

Scary thought when I think about it...

---

### Post by hoarythehedgehog2009 on 2006-04-14
If I use Kubuntu Breezy for the time being can I upgrade to xubuntu dapper (when it comes out as a stable) using apt-get or will i have to reinstall?

---

### Post by Sutekh on 2006-04-14
Sure you can use apt-get.  Its not a terribly hard process.  

All you need to do is change your apt-get sources list so that the repositories look for dapper not breezy.  Its as simple as changing all instances of **breezy** with **dapper**, and then performing the 'dist-upgrade', the command (if you're interested) is
```
sudo apt-get update
sudo apt-get dist-upgrade
``` 
And of course changing the desktop from KDE to XFCE is still just as easy using apt-get.  

Want Xubuntu?
```
sudo apt-get install xubuntu-desktop
```
Too easy.


I think opinion is divided as to the success of using a dist-upgrade.  AYSiu has taken a poll on people's experience, you can check it out here

[Ubuntu Forums -  How did you upgrade from Hoary to Breezy?](http://ubuntuforums.org/showthread.php?t=136921)

I personally will be doing a completely fresh install, as I want to change the structure of my hard discs quite considerably and I just feel after using Breezy for 8 months that a fresh install would be better.

---

### Post by binks on 2006-04-14
ill just add to the above
```
sudo gedit /etc/apt/sources.list
```
and replace breezy with dapper
binks

---

### Post by hoarythehedgehog2009 on 2006-04-14
If I already have Kubuntu or Ubuntu Breezy installed on my computer, do I just type this in the terminal if I want Xubuntu Breezy (not Dapper until it is stable)?

sudo apt-get install xubuntu-desktop

I am fine with using an older version of XFCE until June 1st.  I have a fairly new computer (about 6 months old), but I just like XFCE as a windows manager. I think it looks even better than KDE.  Thanks

---

### Post by Sutekh on 2006-04-14
[quote=hoarythehedgehog200]If I already have Kubuntu or Ubuntu Breezy installed on my computer, do I just type this in the terminal if I want Xubuntu Breezy (not Dapper until it is stable)?[/quote]
Yes that's correct.  

If your apt-get sources are for Breezy then if you install anything with apt-get it will get the packages from the breezy section of the repositories, not the dapper section.  

So if your sources are currently for Breezy, and you can check with```
cat /etc/apt/sources.list
``` then when you use```
sudo apt-get install xubuntu-desktop
```you get Xubuntu for Breezy.

[quote=hoarythehedgehog2009]I have a fairly new computer (about 6 months old), but I just like XFCE as a windows manager. I think it looks even better than KDE. Thanks[/quote]
I have a very high spec computer and I'm not using GNOME/KDE or XFCE.  Just a very light, very customisable windows manager [OpenBox](http://icculus.org/openbox/).  That's one of the best things about Linux/GNU, so many choices!

---

### Post by hoarythehedgehog2009 on 2006-04-15
okay...I think i'll install Gnome Ubuntu Breezy then do the sudo apt code, how long will it take? I will I have to be connected to the internet right?
The change in desktop I mean

---

### Post by OffHand on 2006-04-15
[QUOTE=hoarythehedgehog2009]okay...I think i'll install Gnome Ubuntu Breezy then do the sudo apt code, how long will it take? I will I have to be connected to the internet right?
The change in desktop I mean[/QUOTE]
Yes you do need an internet connection. I'm not sure how long it will take but probably not too long. Goodluck.

---

### Post by hoarythehedgehog2009 on 2006-04-15
[QUOTE=subsonic_shadow]I'm not sure how long it will take.[/QUOTE]

BUMP ANYONE? :(

---

### Post by aysiu on 2006-04-15
Go to a terminal and type ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` Before it installs, it'll tell you all the packages it wants to install and how much space it'll take up and then ask you if you want to proceed.

Let's say it takes up 200 MB more of space. Figure that'll all have to download from the internet. Think about how fast your internet connection is. That's how long it'll take.

---

### Post by hoarythehedgehog2009 on 2006-04-15
Probably about 10 mins in that case :) thanks

---

