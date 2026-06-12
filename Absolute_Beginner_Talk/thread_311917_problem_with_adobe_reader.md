---
title: "problem with adobe reader"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by vroy on 2006-12-03
Hi, I just installed adobe reader by first downloading .rpm file and then using alien and dkpg. Here is exactly what I did
alien AdobeReader_enu-7.0.8-1.i386.rpm
dpkg -i adobereader-enu*.deb
Then in a terminal when I'm running
acroread talk.pdf
I'm getting
bash: /usr/bin/acroread: Permission denied
on the other hand when I'm running
/usr/local/Adobe/Acrobat7.0/bin/acroread talk.pdf
A small box containg the following message is popping up

There was an error while loading the plug-in 'PPKLite.api'
The plug-in failed to initialize

But if I just ignore it and press ok then acroread is opening with my .pdf file.
Is there any way I can get rid of this pop-up? Would you kindly tell me how I can use the command acroread to open my .pdf file instead of writing the full path?
thanks

---

### Post by ron999 on 2006-12-03
Hi vroy

It seems that you have problems with Adobe Acrobat Reader.
It might be easiest to uninstall it and re-install it cleanly using Automatix.
In the meantime, right-click your pdf file and open using document viewer.
:cool:

---

### Post by 5-HT on 2006-12-03
Why bother installing from a .rpm when the package is available in the official repos, and has been tested to work on Ubuntu, unless you're looking for a more recent version? Sticking to official sources, when applicable, can help avoid many headaches. :)

To install from the repos:
```
 sudo aptitude install acroread
```

---

### Post by aysiu on 2006-12-03
> **5-HT said:**
> Why bother installing from a .rpm when the package is available in the official repos, and has been tested to work on Ubuntu, unless you're looking for a more recent version? Sticking to official sources, when applicable, can help avoid many headaches. :)

To install from the repos:
```
 sudo aptitude install acroread
```
Before you can do this, you have to **[enable extra repositories](http://www.psychocats.net/ubuntu/sources)**

---

### Post by vroy on 2006-12-03
Hi,
  Thank you all who replied to my post. But, would somebody kindly tell me how to add repos for acroread in sources.list. Is it safe to add repos through sources.list or should I create another file such as /etc/apt/preferences ?

I've another question regarding xpdf
If I type 
xpdf -fullscreen talk.pdf
 the panels on the top and bottom are still there. How can I get rid of those panels?

---

### Post by aysiu on 2006-12-03
I already linked to it in my last post:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by max.diems on 2006-12-03
In the spirit of Ubuntu, use evince. There's a reason evince is preinstalled and acroread isn't.

---

### Post by vroy on 2006-12-03
I already unchecked all the lines in my sources.list file according to the link, But adobe is not added in repository list yet. That's why when I'm writing
sudo apt-get install acroread
It's showing
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread

 Am I doing anything wrong?

Can you pl tell me how to view a .pdf file in fullscreen in evince?

---

### Post by aysiu on 2006-12-03
> **vroy said:**
> I already unchecked all the lines in my sources.list file according to the link, But adobe is not added in repository list yet. That's why when I'm writing
sudo apt-get install acroread
It's showing
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread

 Am I doing anything wrong?

Can you pl tell me how to view a .pdf file in fullscreen in evince?
After you change your sources.list, you need to run this command: ```
sudo aptitude update
``` before you can run this command: ```
sudo aptitude install acroread
``` The *update* command lets the package manager know what's available in the new repositories.

And to view a PDF in fullscreen, press F11.

---

### Post by vroy on 2006-12-05
Hi,
   I'm sorry for the delay in my reply. Actually, after I did use command 
sudo apt update 
to update the repository list. But, after doing that when I was using 
sudo aptitude install acroread

it was giving the message that it can't find the package acroread. Can you pl explain why I'm facing this problem?

---

### Post by aysiu on 2006-12-05
Can you post the output of these commands? ```
sudo aptitude update
sudo aptitude install acroread
cat /etc/apt/sources.list
``` Do not summarize the output. Just copy and paste it into a post in this thread.

Also, are you, by chance, using PowerPC or AMD64 as your processor?

---

### Post by vroy on 2006-12-05
Hi Aysiu,
        thanks
here is the result I got after running those commands
$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Ign [http://cran.R-project.org](http://cran.R-project.org) dapper/ Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://cran.R-project.org](http://cran.R-project.org) dapper/ Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://cran.R-project.org](http://cran.R-project.org) dapper/ Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [82.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6460B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [15.8kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [968B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [43.6kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [5419B]
Fetched 185kB in 2s (78.1kB/s)
Reading package lists... Done
$ sudo aptitude install acroread
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "acroread"
The following packages have been kept back:
  evince
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/ dapper main restricted
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# CRAN for latest R
# deb [http://cran.R-project.org/bin/linux/debian](http://cran.R-project.org/bin/linux/debian) sarge/
deb [http://cran.R-project.org/bin/linux/ubuntu](http://cran.R-project.org/bin/linux/ubuntu) dapper/
 

I've intel centrino processor.

---

### Post by aysiu on 2006-12-05
Okay. The problem seems to be that even though you have *multiverse* enabled for *dapper-backports*, you don't have the regular *multiverse* repositories enabled.

Can you add these two lines to your /etc/apt/sources.list? ```
deb http://us.archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper multiverse
``` save and then do ```
sudo aptitude update && sudo aptitude install acroread
```

---

### Post by vroy on 2006-12-05
Thank you. It's working now. I've a little problem in viewing the files in fullscreen in acroread. I tried both ctrl L and F11. But still the two panels top and bottom are still there. Can you please tell me how to fix it?
thanks again

---

### Post by aysiu on 2006-12-05
> **vroy said:**
> Thank you. It's working now. I've a little problem in viewing the files in fullscreen in acroread. I tried both ctrl L and F11. But still the two panels top and bottom are still there. Can you please tell me how to fix it?
thanks again
Try Control-L

---

### Post by vroy on 2006-12-06
Hi aysiu,
       I tried control-L. But still the panels are there. Can you tell me something else which might help?

---

### Post by aysiu on 2006-12-06
> **vroy said:**
> Hi aysiu,
       I tried control-L. But still the panels are there. Can you tell me something else which might help?
Unfortunately, no. Control-L works for me. Anyone else have suggestions for vroy?

---

### Post by ron999 on 2006-12-06
Have you tried View > Full Screen vroy?

---

### Post by vroy on 2006-12-06
Hi ron999,
         I tried it. But same thing is happening, I can't get rid of the panel. Do you have any other suggestion?

---

### Post by ron999 on 2006-12-07
Sorry vroy, no more ideas.
View > Full Screen works for me.

---

### Post by aysiu on 2006-12-07
When you say you "can't get rid of the panel"? What panel are you talking about? The borders of Adobe Reader? What desktop environment/window manager are you using? 

Gnome? IceWM? XFCE? KDE? Fluxbox?

---

### Post by vroy on 2006-12-07
Hi aysiu,
         sorry for the delay in my post. Actually, I was referring the panels of my desktop, where I've kept the shortcuts of different applications like terminal, emacs, etc.
It's gnome, which I got as default when I installed ubuntu.

---

### Post by aysiu on 2006-12-07
This is weird, then.

My panel in IceWM doesn't disappear when Adobe Reader goes full screen, but in Gnome, it does disappear. I wonder what the difference is between my Gnome and your Gnome.

---

