---
title: "hellanzb problem"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Borealis on 2007-08-07
Hi Everyone,

I've installed hellabnz onto ubuntu but when i try and launch it I get the following message: (Lunching from alt+f2 does nothing, launching from the terminal gives me this)

```

discodave@discodave-laptop:~$ hellanzb
Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize
discodave@discodave-laptop:~$ 

```

Can anyone help me work out what is wrong please?

Thanks

---

### Post by felicity on 2007-08-07
It doesn't have a GUI, unless you get the optional lottanzb (alpha). (so if you run it out of a terminal it will start a daemon instance). I'm not sure of that error you have, but you may try killing the daemon first (killall hellanzb) and then typing hellanzb in the terminal. Also, did you fill out the /etc/hellanzb.conf file first?

---

### Post by yabbadabbadont on 2007-08-07
I'm guessing that you didn't install the one that is already in the repositories.  Hellanzb requires various "twisted" python packages to be installed in order to work correctly.  I would suggest installing hellanzb from the repos and see if you can get it to work.  (It worked fine for me)

---

### Post by Borealis on 2007-08-07
> **yabbadabbadont said:**
> I'm guessing that you didn't install the one that is already in the repositories.  Hellanzb requires various "twisted" python packages to be installed in order to work correctly.  I would suggest installing hellanzb from the repos and see if you can get it to work.  (It worked fine for me)

Hi there,

I have installed it from the synaptic package manager but there "hellanzb" doesn't require anything else to be installed. Do i have to manually install anything

felicity, yes i did fill that out.

Thanks

---

### Post by yabbadabbadont on 2007-08-07
```
/home/daffy $ aptitude show hellanzb 
Package: hellanzb
State: installed
Automatically installed: no
Version: 0.13-2~feisty1
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 782k
Depends: python (>= 2.3), python-support (>= 0.2), python-twisted-core (>= 2.0), python-twisted-web, par2 (>= 0.4)
Recommends: python-yenc
Suggests: unrar (>= 3.41)
Description: Newzbin (nzb) & BinNews (bns) files downloader and post-processor
 Python application designed for *nix environments that retrieves nzb files and fully processes them. The goal being to make
 getting files from Usenet as hands-free as possible. Once fully installed, all thats required is moving an nzb file to the
 queue directory. The rest; fetching, par-checking, un-raring, etc. is taken care of by hellanzb. 
 
 Homepage: http://www.hellanzb.com/

```
As shown above, it requires at least two "twisted" packages.  However, since you used synaptic, they should have been installed too....  :?

Edit: Which version of hellanzb does synaptic show that you have installed?

---

### Post by Borealis on 2007-08-07
Yeah that does seem to be a bit odd..

synaptic shows 0.10-1ubuntu1 as both my installed version and most up to date from the repo

Cheers

---

### Post by yabbadabbadont on 2007-08-07
Go in to settings->repositories in synaptic and enable the backports repository.  Save the change and close the dialog.  Hit the reload button and then the newer version should be available.

---

### Post by Jimcanoa on 2007-08-07
Try this:
```
sudo apt-get install python-dev python-twisted unrar par2
```
If it doesn't work, try reinstalling hellanzb...

Godd luck!

---

### Post by Borealis on 2007-08-08
> **yabbadabbadont said:**
> Go in to settings->repositories in synaptic and enable the backports repository.  Save the change and close the dialog.  Hit the reload button and then the newer version should be available.

Hi

Do you mean in the third party software tab to have:

ubuntu-backports.mirrormax.net/ hoary-extras 

because I already have that

---

### Post by Borealis on 2007-08-08
> **Jimcanoa said:**
> Try this:
```
sudo apt-get install python-dev python-twisted unrar par2
```
If it doesn't work, try reinstalling hellanzb...

Godd luck!

```

discodave@discodave-laptop:~$ sudo apt-get install python-dev python-twisted unrar par2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-dev is already the newest version.
python-twisted is already the newest version.
unrar is already the newest version.
par2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libcompizconfig0 python-compizconfig
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
discodave@discodave-laptop:~$ 

```

looks like i already have it installed. Tried re-installing but with no luck

Cheers anyway

---

### Post by benfindlay on 2007-11-16
I have exactly the same problems, has anyone found a solution for this?

Cheers
Ben

---

### Post by M3lon on 2007-11-26
had the same problem, found a fix for it on [http://ubuntuforums.org/archive/index.php/t-415320.html](http://ubuntuforums.org/archive/index.php/t-415320.html)

sizzam
April 22nd, 2007, 03:31 PM
I was having the same problem with hellanzb installed from source on a fresh install of Feisty. Here is how I fixed it:

hellanzb is now in the repositories.

First, I got rid of the copy of hellanzb that I installed:

$ sudo rm /usr/bin/hellanzb.py
$ sudo rm -rf /usr/lib/python2.5/site-packages/Hellanzb/
$ sudo rm /usr/etc/hellanzb.*

I then installed hellanzb from the repos. Note that if you are doing a fresh install from the repos, you also need unrar and par2.

$ sudo aptitude install hellanzb unrar par2

I then executed hellanzb from a command line

$ hellanzb

and it worked. After that, I killed hellanzb and configured it. Note that your configuration file is now /etc/hellanzb.conf instead of /usr/etc/hellanzb.conf

Now I add this command to start hellanzb using screen whenever I log into Gnome:

screen -S hellanzb -d -m hellanzb

and I use this shortcut in Gnome to connect to that screen (make a custom shortcut with type 'Application in Terminal'):

screen -R hellanzb

---

### Post by geezerone on 2008-06-30
Old post but still can happen.

I got this error and followed the advice below which fixed it (need latest version of Hellanzb to match python-twisted which is more up-to-date in repositories)

> **Kirobhan said:**
> You need to install the newest version of Hellanzb. As of this post it is "hellanzb-0.13.tar.gz". You can download the newest version from this address: 
[http://www.hellanzb.com/distfiles/](http://www.hellanzb.com/distfiles/)

I had the same problem. I assume because the python-twisted installed from the repositories is a newer version which is causing the the older Hellanzb script to fail.

-Kia

This was found and installed from the following post (post 197 to be exact):

[http://ubuntuforums.org/showthread.php?t=169749&page=20](http://ubuntuforums.org/showthread.php?t=169749&page=20)

Hope this helps someone.

---

