---
title: "Amsn help"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Knapman on 2007-09-29
I tried the autinstaller and it couldnt find the TLS files or something, and I had no idea what that meant so I tried to install the code with terminal.

I  tried this:

[http://amsn-project.net/wiki/Installing_Tarball](http://amsn-project.net/wiki/Installing_Tarball)

The first option didnt work, and the second option wont let me type anything when the password prompt comes up.  Im using Kmess right now but I dont really like it.  Can someone help me get this working please?

Thanks in advance,

Neil! :)

---

### Post by w4ett on 2007-09-29
Why not install from Applications>Add/Remove

---

### Post by Knapman on 2007-09-29
It doesnt show up in the add/remove thing.  I there someway I can add it to it?

---

### Post by meborc on 2007-09-29
why don't you use synaptic to install amsn?

or run ```
sudo apt-get install amsn
```in the terminal?

amsn is in the repos...

EDIT: you need the universe repositories enabled!

---

### Post by w4ett on 2007-09-29
Select Show:  All Available Applications in the upper right.

---

### Post by Knapman on 2007-09-29
I tried to run the code you linked, and im having the same problem.  When it promts for the password I cant type anything.  This seems like a complicated problem. :S

---

### Post by meborc on 2007-09-29
:)

you are not supposed to see the password... just type it and hit enter!

the password id invisible so noone can see the lenght of it... :D so no problem there... try again

---

### Post by Knapman on 2007-09-29
ugh, stuff never works right for me.

In terminal AND in the add/remove thing I get this message:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Knapman on 2007-09-29
> **meborc said:**
> why don't you use synaptic to install amsn?

or run ```
sudo apt-get install amsn
```in the terminal?

amsn is in the repos...

EDIT: you need the universe repositories enabled!

Hmm, I tried to install another MSN alternative and the same thing came up. 

Whats universe repositories? :neutral:

---

### Post by Maestro23 on 2007-09-29
> **Knapman said:**
> Hmm, I tried to install another MSN alternative and the same thing came up. 

Whats universe repositories? :neutral:

[https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by meborc on 2007-09-29
ok... i see you are very new to this... so... go to [www.ubuntuguide.org](www.ubuntuguide.org) and look for the enable extra repositories link (scroll down)

and read this how to install ANYTHING in ubuntu - [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

---

### Post by Knapman on 2007-09-29
> **Maestro23 said:**
> [https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29#head-5bbef89639d9a7d93fe38f6356dc17847d373096)



One problem after another, :(. 

Software Properties does not show up in the list of things under System -> Admin .

I think I fail at linux too badly. :(

---

### Post by Maestro23 on 2007-09-29
> **Knapman said:**
> One problem after another, :(. 

Software Properties does not show up in the list of things under System -> Admin .

I think I fail at linux too badly. :(

What version of Ubuntu are you running as to not be able to find anything?

---

### Post by Knapman on 2007-09-29
> **Maestro23 said:**
> What version of Ubuntu are you running as to not be able to find anything?

Fesity 7.04 (Feisty)

---

### Post by meborc on 2007-09-29
you have to open synaptic package manager from that menu... and THEN configure the sources... :) you will get the hang of it... keep on keeping on!

---

### Post by Maestro23 on 2007-09-29
> **Knapman said:**
> Fesity 7.04 (Feisty)

System >> Software Sources

---

### Post by bigken on 2007-09-29
run this in a terminal 

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install amsn

---

### Post by Knapman on 2007-09-29
When I open Package Manager I get this message again:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report

God...Help...Me...

---

### Post by mrgnash on 2007-09-29
Try Emesene instead ;)

---

### Post by meborc on 2007-09-29
> **bigken said:**
> run this in a terminal 

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install amsn

follow this... as you can READ from the error message, you need to run the first line of code in that post!

---

### Post by Knapman on 2007-09-29
> **bigken said:**
> run this in a terminal 

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install amsn

This almost seemed to work.  But it told me to do this:

apt-get -f install

but it didnt work...


edit:  Here is what it said:

Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  amsn: Depends: imlib11 but it is not going to be installed
        Depends: tcl8.4 but it is not going to be installed
        Depends: sox but it is not going to be installed
        Depends: tk8.4 but it is not going to be installed
        Depends: docker but it is not going to be installed
        Depends: tcltls but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Knapman on 2007-09-29
I did what it said:

neil@XXTXX-MOBILE:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


And thats what I got. What does "are you root" mean?

---

### Post by meborc on 2007-09-29
did you run ```
sudo apt-get -f install
```be sure to use sudo in the front!

root means you have the administrator powers... read more - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Knapman on 2007-09-29
> **meborc said:**
> did you run ```
sudo apt-get -f install
```be sure to use sudo in the front!

root means you have the administrator powers... read more - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)


Didnt do that. Hehe.  A Java agreement thing came up and I dont know how to go to the next thing, or click ok.  it was like a gui inside of terminal.  I have to go, Ill read the replies when I get home. :D

---

### Post by meborc on 2007-09-29
in the java agreement use the TAB key to select yes or ok or whatever you need to select... then enter :)

nice to see you are not discouraged by all this hassle... many people turn around at the first site of trouble... they will never know how good it feels to get over the steepest part of the learning curve and feel that it actually gets easier when you keep remembering new things... :D

see you again sometime on the forums!

---

### Post by bigken on 2007-09-29
you may want to look at [this :)]("http://ubuntuforums.org/showthread.php?t=297676&highlight=amsn+script")

---

### Post by odzk on 2007-09-29
wow dude, it took u so hard just to install amsn, as far as i remember i just click aMSN on the add/remove programs. and tada it worked perfectly well  \\:D/ 

anyway thats whats nice with ubuntu, that is  more challenges, the more problem you get with, the more knowledge you gain with it.

Ubuntu rocks!

---

### Post by Knapman on 2007-09-29
I got it working! Thanks to everyone who helped me figure it out and learn  a little more about linux.  It wont be long until Im back posting my problems! :P

---

### Post by Knapman on 2007-09-29
Im having a little trouble getting the skins to work.  I extracted it, and Im trying to move it to the folder it says to move it to in the install guide, but I get a permission error.  I went into the permissions on the skin and made it read and writeable and all that, but It still wont work...Do I need to be logged into the Root user or something?

Thanks once again,
Neil

---

### Post by Zitron on 2007-10-03
indeed you need to be under root or have sudo before your command as all folders in / are owned by root and can only be used by root.

Anyways,
I was installing amsn and I need to install TLS but I can't seem to find anything about it (on how to install or where to get it).
I am running a 64-bit version of UBUNTU.
I installed amsn using
sudo tar -xvsf amsn*.bz2
etc...
It's installed and all but I can't connect due to my inability to get TLS to work ~_~

---

### Post by crjackson on 2007-10-03
Here, try this [SIZE="4"]**[COLOR="Blue"]_[[COLOR="Blue"][U]aMsn_[/COLOR]]("http://www.getdeb.net/download.php?release=1117&fpos=0")[/U][/COLOR]**[/SIZE]

---

### Post by oomingmak on 2007-10-03
> **Knapman said:**
> Im having a little trouble getting the skins to work.  I extracted it, and Im trying to move it to the folder it says to move it to in the install guide, but I get a permission error.  I went into the permissions on the skin and made it read and writeable and all that, but It still wont work...Do I need to be logged into the Root user or something?
I think the permission relates to the folder that you are trying to put the skins into, rather than the skins themselves. 

The skins folder is in /usr/share/amsn/skins which is a folder requiring administrative (i.e. 'root') privileges.

When you browse to the folder using the standard Nautilus file browser, you are in standard user mode, so you will not be permitted to put your skins in there. So what you need to do is open Nautilus in 'root' mode (which will allow you to write to any folder, even to system ones).

To do this, open a command line terminal and type:

```
gksudo nautilus
```Enter your password when prompted, and a Nautilus window will pop up (titled 'root - File Browser'). You are now in root mode and can now navigate to /usr/share/amsn/skins and paste your skins folders in there.

You might need to re-start aMSN for the skins to show up in the skins list.

---

