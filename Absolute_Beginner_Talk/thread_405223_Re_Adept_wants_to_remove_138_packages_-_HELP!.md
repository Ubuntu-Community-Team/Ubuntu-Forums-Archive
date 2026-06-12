---
title: "Re: Adept wants to remove 138 packages - HELP!"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by tjk on 2007-04-09
I posted the below message at: [http://ubuntuforums.org/showthread.php?p=2424079#post2424079](http://ubuntuforums.org/showthread.php?p=2424079#post2424079)
but I haven't received any solutions to the problem.  Maybe the "Instalation and Upgrade" forum was not the appropriate forum, so I thought I try getting some results here...

> **tjk said:**
> Help!  For some reason Adept Updater shows that it wants to remove 138 packages -- everything from Amarok, to beagle, to k3b, to all of openoffice. It seems that something has gone wrong.  What should I do?

BTW, I am using Kubuntu edgy for AMD64.

---

### Post by tchoklat on 2007-04-09
cancel the upgrdae and use the terminal
 
sudo apt-get update
sudo apt-get upgrade
 
 
and see what it suggests
 
 
tchoklat

---

### Post by tjk on 2007-04-09
Here's the result:

--------------------------------------------------------------------------
xxxxxxxxxxxx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libpango1.0-0: Depends: libpango1.0-common (>= 1.14.8-5) but 1.14.5-0ubuntu1 is installed
                 Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.14.5-0ubuntu1) but 1.14.8-5 is installed
  searchmonkey: Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
E: Unmet dependencies. Try using -f.
-----------------------------------------------------------------

Should I run the command using -f (don't know what it will do), or will it remove all 128 packages?

As well, I see that searchmonkey may be part of the problem ?? - as that was the last package that I was trying to install (under KDE).  Is there a terminal command to just install (oops I mean UNinstall) searchmonkey or would this not solve the problem?

---

### Post by tchoklat on 2007-04-09
sudo apt-get remove searchmonkey
 
but you should run the command
 
apt-get -f install
 
it will offer you the choice of procveeding and will tell you what it is going to do

---

### Post by tjk on 2007-04-10
> **tchoklat said:**
> sudo apt-get remove searchmonkey
 
but you should run the command
 
apt-get -f install
 
it will offer you the choice of procveeding and will tell you what it is going to do

Neither of the above suggestions worked.  I get the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  kdepim: Depends: kitchensync (>= 4:3.5.6-0ubuntu2~edgy1) but 4:3.5.5.dfsg.1-6 is installed
  kitchensync: Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed
               Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3 is installed
  libpango1.0-0: Depends: libpango1.0-common (>= 1.14.8-5) but 1.14.5-0ubuntu1 is installed
                 Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.14.5-0ubuntu1) but 1.14.8-5 is installed
  searchmonkey: Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

PLEASE HELP, this is beginning to be a major pain in the ...

---

### Post by tchoklat on 2007-04-10
sorry I am not being of help, all I can suggest is using aptitude instead of apt-get
 
sudo aptitude -f install

---

### Post by aktiwers on 2007-04-10
I dont know if this can help you, but I once had a huge problem with Synaptic and apt-get.
[http://ubuntuforums.org/showthread.php?t=252762](http://ubuntuforums.org/showthread.php?t=252762)

There is a lot of good suggestions you could try maybe.

---

### Post by tjk on 2007-04-11
The problem has been fixed, so I wanted to post a concluding thread. [B]*(I really would like it if everyone would do this, because there are a lot of situations on this forum that match my own but I never know if they were resolved because no final posted are written.)*
[/B]
Firstly, I'd like to thank those who responded.
Secondly, I'd like to say that the hours of info on this forum didn't help me one bit to  solve my problem... :)  but the worst had to happen before I was fortunate enough to get my system up and running again.

I did all the usual update/upgrade commands and more to try to correct the problem, and in the end I messed up the broken packages even worse ... to the point that my system would not boot into the desktop. Fortunately I still had the command prompt and so I tried issuing a: sudo apt-get install kubuntu-desktop and still I had problems.  Finally I opened aptitude and went through each individual program/module until all the dependencies were resolve (except Amorok-but it seems to be ok)  I installed/updated/removed a large amount of packages and was very concerned that I would have to reinstall Kubuntu from the liveCD.  But once this was done I reboot and yahoo!! everything works again.  Some of the Gnome packages that I installed are no longer around (which may have been part of my problem to begin with), but my system is running faster and some of the java issues that I was having don't seem to be a problem any longer.

I don't recommend this procedure for anyone... it was a last attempt before reinstalling the whole thing, but thankfully it worked for me.

It really would be nice if (k)ubuntu would work at developing a friendlier way of repairing conflicts and broken packages.  Part of this would be if there would be a common standard for packages so that they could be interchanged (I know this won't happen though).  I think I might try using xfce again, since it attempts to be gnome/kde friendly... (I seem to recall that it is possible to run two desktops simultaneously too, which would be interesting) ... oh well, it's all about learning...

---

### Post by tchoklat on 2007-04-14
Good on you. Peased all is working OK for you. With the on-going issues I have had and continue to have with Fiesty I have installed and am using Sabayon Linux 3.3. You may want to look at it!
 
 
cheers,
 
tony

---

