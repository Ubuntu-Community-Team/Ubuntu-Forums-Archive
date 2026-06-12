---
title: "Beryl won't install; can't find package dependencies"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Drpwn on 2007-06-17
EDITED: 
I'm trying to get Beryl to work on Dapper. I followed this walkthrough: [http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036) but I get stuck. I've tried a few other walkthroughs to no avail.

The problem is with the repositories I think.
```
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/Release.gpg  The HT TP server sent an invalid reply header
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/main/binary-amd64/P ackages.gz  Bad header line
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/aiglx/binary-amd64/ Packages.gz  Bad header line
Reading package lists... Done
W: GPG error: http://www.getautomatix.com dapper Release: The following signatur es couldn't be verified because the public key is not available: NO_PUBKEY CC919 A31E23C5FC3
W: GPG error: http://media.blutkind.org dapper Release: The following signatures  couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97 FED8A569E
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```This is my terminal msg.


and later:

```
josh@josh-laptop:~$ sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg li bglitz-glx1 beryl emerald emerald-themes
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
E: Couldn't find package beryl

```

---

### Post by benanzo on 2007-06-17
I think you've got the Beryl repos for Feisty instead of for Edgy.  That could be why your dependencies are messed up.

Open a terminal (**Applications -> Accessories -> Terminal**) and type:
```
gksu gedit /etc/apt/sources.list
```
Find the line that you added for Beryl and change any instance of *feisty* to *edgy*.  Then save and close gEdit.  While still in that terminal do:
```
sudo apt-get update
```
Wait for it to finish then open Synaptic (**Applications -> Administration -> Synaptic Package Manager** and try Beryl again.

Good luck.

---

### Post by Drpwn on 2007-06-17
WOW! I think I have narrowed down the problem; I'm on 6.06. If I'm still dumb enough not to get beryl working I'll edit original post.

Sorry for wasting your time there Benanzo. =( I updated my problem though, I don't know how I missed something that obvious.

---

### Post by Drpwn on 2007-06-17
Any beryl on Dapper help links? Is there a difference between beryl and compiz?

---

### Post by benanzo on 2007-06-19
What kind of graphics do you have?

The easiest and most reliable way to install Beryl is to use the Beryl repositories.  There have been several different Beryl package maintainers rolling their own Ubuntu packages over that last year or so since the split from Compiz.

I would recommend you remove the **blutkind** Beryl repo and use the official ones:
```
sudo gedit /etc/apt/sources.list
```
remove these lines:
```

deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

```
and add this one:
```
deb http://ubuntu.beryl-project.org dapper main
```
Then save and close gedit.
While still in the terminal do:
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```
This will add the necessary GPG key so you can download the Beryl packages.
Now do:
```
sudo apt-get update
```
```
sudo apt-get install beryl beryl-manager emerald emerald-themes
```

The difference between Beryl and Compiz is that Compiz was first (Beryl forked the code) and has been more conservative about the 3D effects.  Beryl has a ton more effects (but might be a little more unstable - I use it everyday without much problem.)  Almost all the cool Youtube videos are of Beryl.

If you have trouble starting Beryl do:
```
glxinfo | grep direct
```
if it says:
```
direct rendering: No
```
Then you have a problem with your graphics driver.

Good luck!

---

### Post by Drpwn on 2007-06-19
Thanks for bearing with me. It's not finding the repo you gave me though. I have an nvidia card and an amd turion64.

here's my output from apt-get update. I bolded what seems important.
```
**josh@josh-laptop:~$ sudo apt-get update**
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:2 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://ubuntu.beryl-project.org dapper Release.gpg
Get:4 http://us.archive.ubuntu.com dapper-backports Release.gpg [191B]
Ign http://ubuntu.beryl-project.org dapper Release
Hit http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://ubuntu.beryl-project.org dapper/main Packages
[B]Hit http://us.archive.ubuntu.com dapper-updates Release
Err http://ubuntu.beryl-project.org dapper/main Packages
  404 Not Found [IP: 80.77.247.17 80][/B]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 4B in 1s (3B/s)
**Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/main/binary-amd64/Packages.gz  404 Not Found [IP: 80.77.247.17 80]**
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

 Previous to that update attempt I think I did get lupine's key.

This is a success, I think: 
```
josh@josh-laptop:~$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
--02:42:22--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 208.113.193.9, 80.77.247.17, 88.191.250.18, ...
Connecting to ubuntu.beryl-project.org|208.113.193.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/x-troff-me]

100%[====================================>] 2,415         --.--K/s

02:42:22 (538.82 KB/s) - `-' saved [2415/2415]

OK

```

These are the ONLY changes made to the sources list, perhaps I screwed those up somehow. Other than that I can't figure out where I'm going wrong. I did a fresh install after killing X yesterday so everything is fairly untouched.
```
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
**deb http://ubuntu.beryl-project.org dapper main**
```

updating:
[B]josh@josh-laptop:~$ glxinfo | grep direct
Error: couldn't find RGB GLX visual[/B]

Is this the culprit? Or does that install from beryl-project.org dapper main?
My Xorg.conf has my graphics card listed as vesa, but when I try to change it to nvidia it results in x not loading. I don't think that would interfere in simply getting the beryl package though.

---

### Post by Ptero-4 on 2007-06-20
did you install the nvidia binary drivers?

---

### Post by Drpwn on 2007-06-20
I figured everything out. I uninstalled Ubuntu and installed Sabayon. Everything works flawlessly. (solved) ;-)

---

