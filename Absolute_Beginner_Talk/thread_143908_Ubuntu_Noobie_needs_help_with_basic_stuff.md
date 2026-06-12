---
title: "Ubuntu Noobie needs help with basic stuff"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Justin Holt on 2006-03-13
Hello everyone,
I am a complete noob to ubuntu and the whole Linux thing.  I need help with one of the most basic things.  How do i get things like firefox to update to the new 1.5 and how to install things like amaroK.  If you can help me thanks a lot. :-k

---

### Post by aysiu on 2006-03-13
Firefox:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

AmaroK:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jbaloul on 2006-03-13
you mite wanna start getting familiar with the GUI package manager as a start.
It is called synaptic and to use it either find it in your programs menu or open a shell (command line) and use tis command:
sudo synaptic

have fun!
jb

---

### Post by Justin Holt on 2006-03-13
Well this could be a problem...here is what I get when I enter stuff in the terminal...I think i messed up the install or something...

justin@ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Fetched 1B in 0s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
justin@ubuntu:~$ sudo apt-get install firefox
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

See what you can make of that

---

### Post by Ubuntuud on 2006-03-13
The nice thing of linux is that it says what the problem is, it says "is another process using it?". The most common cause of this is that you have or synaptic running or that other software installer (I don't know if it even has a name).

---

### Post by Justin Holt on 2006-03-13
well like ubuntuud suggested i closed the synaptic package manager and was able to do something...but i look at the link provided for amaroK by aysiu and i still get an error message of:

justin@ubuntu:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

hmmm.....?

---

### Post by aysiu on 2006-03-13
Sounds as if something's wrong with your repositories list.

Get a fresh one:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by jjf on 2006-03-13
Did you try using Synaptic to get it?  (System > Administration > Synaptic Package Manager).  I did a search for "amarok" in mine and see it there for installation.

Make sure that you've added the extra repositories, since that may be why you're getting the error message with apt-get (in Synaptic, Settings > Repositories > Add; click to add the Universe and Multiverse).

---

### Post by Klaidas on 2006-03-13
[QUOTE=Justin Holt]Hello everyone,
I am a complete noob to ubuntu and the whole Linux thing.  I need help with one of the most basic things.  How do i get things like firefox to update to the new 1.5 and how to install things like amaroK.  If you can help me thanks a lot. :-k[/QUOTE]
I'd recommend [Automatix]("http://www.ubuntuforums.org/showthread.php?t=114251") for installing the new firefox. If you are new, it will be a lot easier :)

---

### Post by Justin Holt on 2006-03-13
ok...so the automatix thing, um...i follow a link that is the link provided by Klaidas and it shows as an invalid link....hmmm

the link is [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

thanks for everything guys

---

### Post by bobpur on 2006-03-13
[QUOTE=Justin Holt]ok...so the automatix thing, um...i follow a link that is the link provided by Klaidas and it shows as an invalid link....hmmm

the link is [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

thanks for everything guys[/QUOTE]
I Checked out what Amarok was and thought I'd like to have it in my computer.
"sudo apt-get install amarok" will work. The only thing I can tell you is; Enable Respositories then update and it should work.
That's worked for me. 


" If it ain't broke, fix it 'til it is then re-install!"

---

### Post by jbaloul on 2006-03-13
copy and paste this into your shell

```
echo "creating backup of sources.list before changing to universe"
sudo cp -vpr /etc/apt/sources.list /etc/apt/sources.list.bkup
echo "changing sources.list now for installation of pkgs"
echo "
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiversedeb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
" > /etc/apt/sources.list
echo "installing required pkgs from universe"
sudo apt-get update
sudo apt-get install amarok


```

that should do the trick.

jb

---

### Post by Justin Holt on 2006-03-13
thanks but i got it to work by entering 

sudo apt-get install kde
sudo apt-get install amarok

that fixed it about and hour later

---

### Post by Brunellus on 2006-03-13
[QUOTE=Justin Holt]thanks but i got it to work by entering 

sudo apt-get install kde
sudo apt-get install amarok

that fixed it about and hour later[/QUOTE]
yup.  

"terminal" is what that program tries to emulate (a physical terminal, y'know, with a keyboard, a phosphorus screen, and a serial interface to the main computer--yeah.  old school stuff).  "Shell" is the thing that interprets commands.

---

