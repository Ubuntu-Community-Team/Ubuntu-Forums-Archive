---
title: "HOw do you install a program?"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-04-16
I want to install some programs that are for linux but i don't know how?
I know,I am  a noob at linux......
Like for firefox it says to install to the /opt/ folder but when i extract the tar.gz it says i don't have write permissions...It says only root and the usergroup root does

---

### Post by ubernoob on 2006-04-16
then you have to write "sudo" in front of the commands

---

### Post by Jagot on 2006-04-16
Follow the instructions exactly on this Wiki for Firefox:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

Let us know what other programs you want to install and we'll see if we can help.

---

### Post by zxcvbnm on 2006-04-16
I have Kubuntu KDE so it is not in terminal....How would i extract and install the programs to it in terminal or be a super user without being in terminal

This is what i get
tar: firefox-1.5.02.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by jazzmuzik on 2006-04-16
[QUOTE=zxcvbnm]I want to install some programs that are for linux but i don't know how?
I know,I am  a noob at linux......
Like for firefox it says to install to the /opt/ folder but when i extract the tar.gz it says i don't have write permissions...It says only root and the usergroup root does[/QUOTE]

Before installing something the hard way, first look to see if the program is already offered in the repositories. Run Synaptic (System, Administration, Synaptic Package Manager). Synaptic is a package (program) installer/deinstaller. Use its search function. If you see what you want to install, click it to Mark it. Then press apply.

---

### Post by aysiu on 2006-04-16
If you want to install Firefox 1.5.0.2 and find the Wiki instructions too daunting, try this script:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

For basic installation needs, read this:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by zxcvbnm on 2006-04-16
I have ADEPT package manager.......... Is there an easy way to do something.......

EDIT: thanks i will try those links

---

### Post by aysiu on 2006-04-16
[QUOTE=zxcvbnm]I have ADEPT package manager.......... Is there an easy way to do something.......

EDIT: thanks i will try those links[/QUOTE] Adept is terrible. If, for example, you want to remove a package, and it will subsequently remove fifty other packages, Adept will not warn you those fifty packages are to be removed.

Use Synaptic Package Manager (which, actually, can be installed using Adept--the package is called *synaptic*), apt-get or aptitude (these last two are command-line versions of Synaptic and Adept).

---

### Post by zxcvbnm on 2006-04-16
Ok but it says that Adept is read only you have to run as root to install packages.....

I also tried  doing it in terminal and it says......... that it can't be locked and asks if another process is running it..


Oh and also if possible i would like to install and update my packages without using terminal...So to do that i would have to run as root

---

### Post by zxcvbnm on 2006-04-16
Bumpity Bump Bump

---

### Post by htinn on 2006-04-16
zxcvbnm, open Konsole and run this:

sudo apt-get install Synaptic

Then just use Synaptic to install for now.

---

### Post by aysiu on 2006-04-16
[QUOTE=zxcvbnm]Ok but it says that Adept is read only you have to run as root to install packages.....[/quote] Are you running Adept from the command-line or the launcher? If you're launching from the command line, use the command ```
kdesu adept
```
> 
I also tried  doing it in terminal and it says......... that it can't be locked and asks if another process is running it.. You can't use apt-get or aptitude while Adept or Synaptic is open.

---

### Post by zxcvbnm on 2006-04-16
Thanks for the reply but that command kdesu adept only opens the program and it still says read only..How do i close it completely because i exited out of it but it still  says another process is  running

---

### Post by zxcvbnm on 2006-04-16
Bumpit Bump Bump 



Happy Easter!!!!!!!

---

### Post by htinn on 2006-04-16
You might try restarting the computer if all else fails.

---

### Post by aysiu on 2006-04-16
Happy Easter.

By the way, it's not necessary to bump a thread after twenty minutes, or even after an hour.

If you want to make sure Adept is totally dead, press Control-Alt-F1, log in, and type ```
sudo killall adept
```

---

### Post by zxcvbnm on 2006-04-16
Sorry i am kind of an impatient guy...LOL

---

### Post by Papa-san on 2006-04-16
I am a noob as well. I have only been ubuntized for a month now. I had never used anything like 'terminal' before. The windows equivalent is when you click Start > Run, and type Cmd then enter. 
I was TERRIFIED of it... (ubuntu's terminal)
Do NOT be afraid, Grasshopper!
in terminal (Applications > Accessories > Terminal):
```
 sudo apt-get install synaptic 
```

will do you right! Another suggestion I would make instead would be to start with Automatix. This will reduce the number of challenges you may be facing by at least half! That one (Automatix) helps take a few important programs and allow a windows trained computer user to handle them...

---

### Post by aysiu on 2006-04-16
I'm with Papa-san.

I would advise you to do ```
sudo apt-get update
sudo apt-get install synaptic
``` though.

And, make sure you get Automatix for Kubuntu instead of Ubuntu.

---

### Post by Papa-san on 2006-04-16
Hehehe.... I'm glad someone caught the Kubuntu thing... I sure didn't!

---

### Post by zxcvbnm on 2006-04-16
Thanks..umm i got synaptic but whenever i install a package it says this


E: nfs-common: subprocess post-installation script returned error exit status 1
E: nfs-kernel-server: dependency problems - leaving unconfigured
E: ltsp-server: dependency problems - leaving unconfigured

---

### Post by aysiu on 2006-04-16
That's an ugly error I've never seen before.

What does your /etc/apt/sources.list file look like? Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by cremen02 on 2006-04-16
I just installed Ubuntu and I've been trying to install Banshee to be able to sync up with my Ipod and I've read many of the online guides but none seem to help; I'm just a noob who needs some help learning

---

### Post by zxcvbnm on 2006-04-16
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

 ## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverseharry@ubuntu:~$


Ok but i just updated this like a couple of minutes ago for Automatix......So it might be different

---

### Post by zxcvbnm on 2006-04-17
Also what is Automatix..Isn't it the same as synaptic? Just less packages?

---

### Post by aysiu on 2006-04-17
[QUOTE=zxcvbnm]Also what is Automatix..Isn't it the same as synaptic? Just less packages?[/QUOTE] Your sources.list looks good... unfortunately (meaning I have no idea why you're running into that error).

Automatix is a script that has a graphical frontend where you can pick some of the most popular software and codecs to be installed and they will be. It's sort of like Synaptic, but not exactly.

---

### Post by zxcvbnm on 2006-04-17
HELP!!!!!!!! I went to bed last night and when i woke up and turned on my computer And was loading kubuntu......It had alot of errors.....

It couldn't find my root and source list and some other errors...........It would only log me in as the /home directory and only in terminal so i couldn't get into the desktop...
I don't know what could of happened This sucks

Oh and it says something with postinst script...whitch if you look above  this thread the errors i posted 1 had to do with post instalation

---

