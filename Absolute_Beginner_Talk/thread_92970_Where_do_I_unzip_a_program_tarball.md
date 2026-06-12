---
title: "Where do I unzip a program tarball?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by eric.stone on 2005-11-20
This is my first try at extracting a tarball!  I have "kazehakase-0.3.2.tar.gz" and don't know where to place it before extracting it.   Should I use the command line?  If so, what commands should I use?
Thanks again,
Eric

---

### Post by bk452 on 2005-11-20
I right-click on the archive and use the 'extract here' feature.

---

### Post by eric.stone on 2005-11-20
Where will it extract to?  Will it know where to go?
Thanks,
E

---

### Post by aysiu on 2005-11-20
Why are you extracting a tarball? Ditch the tarball--throw it in the trash--you don't need it.

Why not just install it through Synaptic/apt-get?

Follow the instructions in the first link in my signature (it allows you to have extra sources for software).

Then to install it through apt-get, type this in a terminal ```
sudo apt-get update
sudo apt-get install kazehakase
``` You can also do this graphically through Synaptic Package Manager (see screenshot and the second link in my sig).

---

### Post by suRoot on 2005-11-20
I think aysiu is right, but remember - there are times when you need to extract an archive for one reason or another.

As someone else pointed out, you can simply right-click the archive & select "Extract Here" from the context menu.  It will create a directory & extract the contents of the archive in to that directory.  The new directory will be in the same location as the archive.  For instance, if you downloaded the file to your desktop, the extracted archive would also be on your desktop.

If you wanted to do it through a console, assuming again you downloaded to your desktop:

```

$ cd ~/Desktop/
$ tar -zxvf foo.tar.gz
```

which will do the exact same thing as the "Extract Here" context menu

---

### Post by eric.stone on 2005-11-20
Thank you!  Where can I find the program after I have followed your instructions?

---

### Post by bk452 on 2005-11-20
> Where will it extract to? Will it know where to go?
Thanks,

It will extract to the directory that you're in.  If you're in "My Pics", it will extract to "My Pics".  Hope this helps.  But aysiu is right if you're trying to compile something.  Using Synaptic and the repositories is much easier than trying to compile from source.  Dependency hell can drive you nuts. Synaptic and apt-get take care of those dependencies for you.

---

### Post by eric.stone on 2005-11-20
I guess the better question is where *should* I extract the program so that it is the right place for web browsers?
Thanks,
E

---

### Post by aysiu on 2005-11-20
[QUOTE=eric.stone]Thank you!  Where can I find the program after I have followed your instructions?[/QUOTE] Programs usually will be in the Applications menu. It may not refresh right away. If you want to force a refresh, run the command ```
killall gnome-panel
``` If it doesn't refresh after that, you can edit the Applications menu yourself or add a launcher in the panel with the command that's usually the name of the program: ```
kazehakase
```

---

### Post by aysiu on 2005-11-20
[QUOTE=eric.stone]I guess the better question is where *should* I extract the program so that it is the right place for web browsers?
Thanks,
E[/QUOTE] You don't need to extract anything. apt-get or Synaptic take care of *everything* for you--it will download the installer file, all the installer file's dependencies, unpack and install everything for you.

---

### Post by eric.stone on 2005-11-20
Followed your original code and got the following message after the "sudo apt-get install kazehakase" command:

The following packages have unmet dependencies:
  kazehakase: Depends: mozilla-browser (>= 2:1.7.6) but it is not going to be installed
E: Broken packages

Thanks,
E

---

### Post by aysiu on 2005-11-20
Are you using Hoary (Ubuntu 5.04)? Because my Synaptic is showing Mozilla Browser version 1.7.12 (I'm on Breezy).

---

### Post by ecobuntu on 2005-11-20
Sounds like it's broken...
If you still have that tarball

tar xvzf package.tar.gz
cd package
make
sudo make install

And you should be in business unless there are dependencies that you don't meet.  But I always run apt-cache search package before I resort to tarballs

---

### Post by eric.stone on 2005-11-20
HH.  What's the best way to upgrade to breezy b?
E

---

### Post by m0biu5 on 2005-11-20
I think you all missed the original question, which is a good one to answer. Should you have a program that is not in the repos, where do you extract it and keep it so that you can run it? I assume its preference, but what is the norm?

---

### Post by aysiu on 2005-11-20
[QUOTE=ecobuntu]
And you should be in business unless there are dependencies that you don't meet.[/QUOTE] Isn't it pretty clear he *does* have dependencies that aren't met?

---

### Post by aysiu on 2005-11-20
[QUOTE=m0biu5]I think you all missed the original question, which is a good one to answer. Should you have a program that is not in the repos, where do you extract it and keep it so that you can run it? I assume its preference, but what is the norm?[/QUOTE] Actually, the original question wasn't "I can't find this in the repositories, so how do I install a tarball?" The question kind of assumed a tarball is the only way you install a program. That program actually *is* in the repositories!

For all the different ways to install programs in Ubuntu, I've written this up:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by aysiu on 2005-11-20
[QUOTE=eric.stone]HH.  What's the best way to upgrade to breezy b?
E[/QUOTE] Get the Breezy sources.list (see the first link in my sig), then run these two commands ```
sudo apt-get update
sudo apt-get dist-upgrade
``` **Warning**: it may take a long time, even if you have broadband.

By the way, when you have Breezy, this is what's supposed to happen: ```
sudo apt-get install kazehakase
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  mozilla-browser
Suggested packages:
  migemo latex-xft-fonts
Recommended packages:
  estraier mozilla-psm
The following NEW packages will be installed:
  kazehakase mozilla-browser
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 9810kB of archives.
After unpacking 30.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy-updates/main mozilla-browser 2:1.7.12-1ubuntu1 [9180kB]
Get:2 http://archive.ubuntu.com breezy/universe kazehakase 0.2.8-1ubuntu2 [630kB]
Fetched 9810kB in 1m4s (153kB/s)

Preconfiguring packages ...
Selecting previously deselected package mozilla-browser.
(Reading database ... 121911 files and directories currently installed.)
Unpacking mozilla-browser (from .../mozilla-browser_2%3a1.7.12-1ubuntu1_i386.deb) ...
Selecting previously deselected package kazehakase.
Unpacking kazehakase (from .../kazehakase_0.2.8-1ubuntu2_i386.deb) ...
Setting up mozilla-browser (1.7.12-1ubuntu1) ...
Updating mozilla chrome registry...done.

Setting up kazehakase (0.2.8-1ubuntu2) ...
```

---

### Post by eric.stone on 2005-11-21
Thank you all very much for your help last evening.  I got called away to help with a fussy baby and I never got back.  I'm going to move to breezy this week and keep on learning linux.  Special thanks to Aysiu!
Higest regards!
ERIC

---

### Post by m0biu5 on 2005-11-21
[QUOTE=aysiu]Actually, the original question wasn't "I can't find this in the repositories, so how do I install a tarball?" The question kind of assumed a tarball is the only way you install a program. That program actually *is* in the repositories!

For all the different ways to install programs in Ubuntu, I've written this up:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]


I didn't say that, I said assuming there is a program that has no .deb to be found, where do you extract it?

---

