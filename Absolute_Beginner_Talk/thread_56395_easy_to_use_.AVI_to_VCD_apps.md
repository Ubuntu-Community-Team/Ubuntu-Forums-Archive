---
title: "easy to use .AVI to VCD apps?"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by xnszxdotnet on 2005-08-12
I was wondering if there is a easy to use GUI version of an app that can convert .avi files to VCD?

I was trying to get avidemux to install but having problems doing so. I don't know what I 'm do wrong so I want to find somthing else. I searched and found alot of windows apps.    Can I install those using Wine?

thanx

---

### Post by KingBahamut on 2005-08-12
I believe if you cruise out to freshmeat.net , youll find a perl script called avi2mpg , thatll convert most avi's to mpg qual vid, then just use vcdimager ( I think that K3b uses this by default for its vcd creation ) to create your video cd.  Havent had much experience other than that though. 

Anyone else?

---

### Post by maruchan on 2005-08-12
How about something like this? Looks pretty cool to me:

[http://kde-apps.org/content/show.php?content=16839](http://kde-apps.org/content/show.php?content=16839)

---

### Post by maruchan on 2005-08-12
Okay, I had to try it, now that I found it. It's actually pretty simple to use! I am encoding an SVCD right now from an .avi file. 6 hours left!

Notes:

-I downloaded the .rpm from SourceForge and converted it to .deb with alien, then installed the .deb.
-You need to also install mjpegtools, cdrdao, and transcode (easy, use apt-get)
-Make sure your source video is not stored on read-only media, like a read-only WinXP partition. For some reason this was not working for me.
-I can't double-click folders in the file-open dialogs, for some reason (?), so I select and use the enter key to open them. Kind of a pain, but I have no idea what a fix for this might be.

---

### Post by xnszxdotnet on 2005-08-12
I've changed the .rpm to a .deb so how do I install the .deb?

I keep getting errors add/remove programs doesn't seem to be working. and synaptic doesn't see it.

---

### Post by KingBahamut on 2005-08-12
[QUOTE=xnszxdotnet]I've changed the .rpm to a .deb so how do I install the .deb?

I keep getting errors add/remove programs doesn't seem to be working. and synaptic doesn't see it.[/QUOTE]
 go to command line and type

sudo dpkg -i <name of the newly named debfile>

---

### Post by maruchan on 2005-08-12
Okay, here are the steps:

Convert .rpm to .deb:

```
sudo alien -d kavi*.rpm
```

Install .deb file:

```
sudo dpkg -i kavi*.deb
```

Make sure other packages are installed:

```
sudo apt-get install mjpegtools
sudo apt-get install cdrdao
sudo apt-get install transcode
```

If this isn't working, try substituting your /etc/apt/sources.list with mine:

Run:

```
sudo gedit /etc/apt/sources.list
```

Save a backup copy first, like "sources.list.backup"

Then replace what you have with this:

```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse
#deb-src http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backup Security Mirrors
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backports
#deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Finally, run "sudo apt-get update" and try those apt-get steps again.

---

### Post by xnszxdotnet on 2005-08-12
OK everything seemed to install.

is there a way that I can put the app in my menu?

or how do I run this app?

---

### Post by maruchan on 2005-08-12
You can run it by typing kavi2svcd in a terminal window, or you can right-click your desktop to make a new shortcut (I'mat work now so I can't remember what it's called) there. I think you can also use a menu-editor called "smeg" (sudo apt-get smeg?) to add it to your main programs menu.

---

### Post by xnszxdotnet on 2005-08-12
I tried to run it like this:

```
kavi2svcd *.avi
``` 

I got this error. Do I have the syntax right ?
no man pages. ??

```
kavi2svcd: error while loading shared libraries: libkdeui.so.4: cannot open shared object file: No such file or directory
```

---

### Post by maruchan on 2005-08-12
Have you tried running it without the *.avi at the end?

I also have Kubuntu installed (in fact, I run it within Kubuntu) so you might need to install more libraries for it to work. Try searching for that libkdeui.so.4 library in Synaptic!

---

### Post by xnszxdotnet on 2005-08-14
I tried searching for libkdeui.so.4 library in Synaptic and found nothing.

I did a quick google for libkdeui.so.4 found out that it's a resource for a RPM. If I was to be able to find it and install it, wouuld it even work?

I though alien took care of this??

---

### Post by rubengs on 2006-02-08
To easily install kavi2svcd add these repositories to your sources.list file: 

## archive.kubuntu.de / archive.czessi.net
## unofficially repository powered by Czessi.net and Kubuntu Germany
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy stable stable-updates
deb-src [http://archive.czessi.net/](http://archive.czessi.net/) breezy stable stable-updates
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy testing testing-updates
deb-src [http://archive.czessi.net/](http://archive.czessi.net/) breezy testing testing-updates
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy unstable unstable-updates
deb-src [http://archive.czessi.net/](http://archive.czessi.net/) breezy unstable unstable-updates

---

### Post by FISH on 2006-02-09
Hi I would like to recommend TOVID, ive used it for quite some time.

[http://tovid.berlios.de/en/](http://tovid.berlios.de/en/)

it was even featured in LinuxFormat magazine!

---

### Post by jtpratt on 2006-03-22
The video conversion scripts for nautilus would work best for this.  Find the link to them and more ubuntu video conversion and burning help [here in my guide]("http://smorgasbord.net/convert_video_linux").

---

