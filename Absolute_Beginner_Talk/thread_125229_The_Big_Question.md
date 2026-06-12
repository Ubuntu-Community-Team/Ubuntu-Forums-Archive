---
title: "The Big Question"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-02-03
I recently purchased Sibelius for my computer and I really need it on my Linux machine (as this is the one I work on) so how would I go about configuring UBunutu so I can install and use it please?

I know this is a bit of a large question but any help will be appreciated to the greatest extent.

Many thanks.

---

### Post by az on 2006-02-03
[http://www.sibelius.com/products/sibelius/](http://www.sibelius.com/products/sibelius/)

Is that what you are talking about?

It seems to be proprietairy software written for windows or mac.  Maybe you can install wine (enable the universe repository) and try to run it through that.  Wine can run some windows software in linux.


[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
Once you enable the universe repository and update, perhaps there is equivalent software written for linux.  Search through synaptic to see what is available.

---

### Post by Dr Von Bon Bon on 2006-02-03
Yeah it is that.

I'll have a try with wine and see what happens thanks.

---

### Post by Dr Von Bon Bon on 2006-02-03
This is what happened when I tried to install Wine;

```
god@Callum:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.0MB of archives.
After unpacking 56.0MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Err http://wine.sourceforge.net binary/ wine 0.9.6-winehq-1
  404 Not Found
Failed to fetch http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb  404 Not Found
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Any help please?

I've switched all repositories on.

---

### Post by az on 2006-02-03
> **Dr Von Bon Bon]This is what happened when I tried to install Wine said:**
> ? y
Err http://wine.sourceforge.net binary/ wine 0.9.6-winehq-1
  404 Not Found
Failed to fetch http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb  404 Not Found
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Any help please?

I've switched all repositories on.
The mirrormax repositories for backports are no longer valid.  Are you running Hoary or breezy?  Anyway, disable them, update and you should be fine.

---

### Post by BenTyreman on 2006-02-03
Firstly, you will need to change the backports mirrors to
```
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
```
as the mirrormax mirrors aren't used anymore.

Then, run
```
sudo apt-get update
```
again, as the version of wine it is trying to install is not the latest one.

Finally, run
```
sudo apt-get install wine
```
to install the latest version (0.9.7).

---

### Post by Dr Von Bon Bon on 2006-02-03
I'm running Breezy.


How do I go about changing or disabling the repositories please?

---

### Post by BenTyreman on 2006-02-03
Easiest way is to fire up a terminal (Applications -> Accessories) and type in
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Dr Von Bon Bon on 2006-02-03
I've done that and I've installed Wine and got on to installing my thing but I need to access where it has been installed. Could you tell me where please?

---

### Post by az on 2006-02-03
If you want to run foobar.exe in wine, you just need to open a terminal and run

wine foobar.exe


However, if you have wine installed, Gnome will know that.  If you click on an exe, gnome will use wine to open it, by default.  You can right-click on the exe to change what application is used to open it.  Cedega is another version of wine (that is in of itself proprietary) that runs games better than wine, for example.

Wine is not a graphical application, in of isself.

---

### Post by Dr Von Bon Bon on 2006-02-03
Thanks but I already worked out how to run a program it's just the fact that I need to find where the file is installed and gain access to the folder that it's in.

---

### Post by az on 2006-02-03
Depending on the installer, it usually makes a launcher for you.

Look in ./.wine

Dotfiles and directories (/home/daddy/.wine) are hidden.  You need to tell nautilus to show hidden files and directories.

Sorry, I though you were asking where wine was installed.

---

### Post by Zahrber on 2006-02-03
Well were it was installed would have been up to you when you installe the program.

Wine created a Windows setting so to speak....

On my system I have a local Drive_C\Program Files directory for installing all windows programs which is where I install all mine...so I can keep them organized and easy to find..

I open a terminal and just cd to the Program Files directory and then to the directory of the program...

---

