---
title: "playing a windows game on linux"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-29
I have a game called commandos 3 for windows.  I was wondering if someone could help understand how I would install this game and play it on my ubuntu machine.

---

### Post by aysiu on 2005-10-29
I don't know much about gaming, but my guess is [Cedega](http://www.transgaming.com/) is the answer.

---

### Post by Mustard on 2005-10-29
[QUOTE=aysiu]I don't know much about gaming, but my guess is [Cedega](http://www.transgaming.com/) is the answer.[/QUOTE]

As a gamer, I would wholeheartedly agree that cedega is the best option.

---

### Post by kingsidy on 2005-10-30
first let me say that commandos is an excellent game (having played and finished all releases). as far as playing on linux, like everybody else's suggestion, you'll probably have to use cedega.

---

### Post by generalstoner on 2005-10-30
Is there a way to find that for free or is there a free application out there.

---

### Post by gpw797 on 2005-10-30
Go to cedega webpage and see if it works in game database

[http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by Kimm on 2005-10-30
You can try to use Wine ([http://www.winehq.com)](http://www.winehq.com)), Cedega is based on it, and some games work with it (sometimes better). Its free so, go ahead and try it. Also, there is something called CVS Cedega and thats free, I dont know how to get it however.

I do recoment Cedega aswell, as I have used it. But try Wine first.

---

### Post by generalstoner on 2005-10-30
I cant seem to figure out how to install wine, does anyone have a easy guide for breezy

---

### Post by shandar on 2005-10-30
```
sudo apt-get install wine
``` and you're set. Then run winesetup to configure it.

Or, follow these instructions (found at the winehq.com website by clicking download...): [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by generalstoner on 2005-10-30
I did the apt install and now I cant find the program, it isnt in my app list or in my application menu tool

---

### Post by Kimm on 2005-10-30
open a terminal and type:
sudo gedit /etc/apt/sources.list

(or if your using kde, replace gedit with kwrite)

then add this to the end of the file and click save, then exit gedit.

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

now, type this in your terminal:

sudo apt-get update
sudo apt-get install wine

when thats done, type this.

wget [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-2.1.2-jo.i386.rpm](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-2.1.2-jo.i386.rpm)
alien winetools-2.1.2-jo.i386.rpm

then type:

sudo dpkg -i <generated filename>

When thats done, run WineTools by typing: wt2, run base setup to install IE and so forth.

Now you should be able to run some windows apps by typing wine <progname>

Hope that got it all sorted out :)

---

### Post by wishyjr on 2005-10-30
ok, when i get upto the **sudo apt-get install wine** part i get this:

paul@ubuntu:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


..now ive double checked my sources list and its correct but still no dice! can you help me?

---

### Post by generalstoner on 2005-10-30
when I get here "
wget [http://ds80-237-203-29.dedicated.hos....2-jo.i386.rpm](http://ds80-237-203-29.dedicated.hos....2-jo.i386.rpm)
alien winetools-2.1.2-jo.i386.rpm

then type:

sudo dpkg -i

followed by the generated filename.

When thats done, run WineTools by typing: wt2, run base setup to install IE and so forth."
 I get lost, I enter dpkg -i and it brings up a help menu and I dont know what to do form there.

---

### Post by Kimm on 2005-10-30
> 
ok, when i get upto the sudo apt-get install wine part i get this:

paul@ubuntu:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


..now ive double checked my sources list and its correct but still no dice! can you help me?


Hmm... thats strange, are you sure you added the lines?
and you must run:

sudo apt-get update

before you try to install.

> 
I enter dpkg -i and it brings up a help menu and I dont know what to do form there.


oh, let me rephrase:

it should be:

sudo dpkg -i <generated filename>

:)

---

### Post by generalstoner on 2005-10-30
do I actually type <generatedFileName> or do I have to find it, I have no idea were to look.

root@darren:/home/darren# sudo dpkg i-winetools-2.1.2-jo.i386.rpm.2
dpkg: need an action option

I tried that out and that is the response I get.

---

### Post by Kimm on 2005-10-30
no no, after you type:

alien winetools-2.1.2-jo.i386.rpm

you should get a message, something like:

"winetools_2.1.2_i386.deb generated"

(thats probably not what is sais, but something similar).

and by <generated filename>, in this case, I mean "winetools_2.1.2_i386.deb"

get it? :smile:

---

### Post by wishyjr on 2005-10-31
ok, heres my sources.list . Can you see anything wrong with it?

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Hoary Extras (October 16 2005: Breezy Extras are not curently available)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
------------------------------------------------------------------------

and yeah, i ran sudo apt-get update too!

im just at a loss with this

---

### Post by Kimm on 2005-11-01
not realy...

However, are you using a Normal PC... or eighter an AMD64 computer or a PPC Computer (Mac)?
Since the programs run on the CPU wine can only run on an x86 processor (or on an AMD64 if the rest of the system is x86... I think)

---

