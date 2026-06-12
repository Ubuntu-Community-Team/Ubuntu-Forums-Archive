---
title: "How do you install a .deb not in the repositories? (Opera, for example)"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by MoLeak on 2005-10-18
It seems to be that no one on any Linux forum so far willing to answer this question.  I recently downloaded Opera for Ubuntu (breezy) and it sits on my desktop.  Not a place I would normally download to but I got an error for the archive manager. ( I'll get back to that one later.)  I want to install this package but I have no idea how to make this happen.  Some issue with Deb not supporting the archive type.  what ever deb is.

What do I do?

-MoLeak

---

### Post by NicS on 2005-10-18
.deb is the type of file for packaging applications in some Linux distros (comes from Debian)
so you cannot open it with an archive manager.
It's like opening a .cab or .iso with winrar on windows.

so to install this, I know there is an extension that gives an option to install deb files in your context menu, or even scripts to put in your nautilus-scritps directories, but I'm sorry I only know the command line:
Open a Terminal (Applications Accessoires)
Then: cd <the directory where you .deb is>
Then: sudo dpkg -i <the name of the .deb file>
sudo is to get administrator privileges
dpkg is the tool to install a single deb file

Hope this helps

PS: Consider reading ubuntuguide.org

---

### Post by MoLeak on 2005-10-18
[QUOTE=NicS].deb is the type of file for packaging applications in some Linux distros (comes from Debian)
so you cannot open it with an archive manager.
It's like opening a .cab or .iso with winrar on windows.

so to install this, I know there is an extension that gives an option to install deb files in your context menu, or even scripts to put in your nautilus-scritps directories, but I'm sorry I only know the command line:
Open a Terminal (Applications Accessoires)
Then: cd <the directory where you .deb is>
Then: sudo dpkg -i <the name of the .deb file>
sudo is to get administrator privileges
dpkg is the tool to install a single deb file

Hope this helps

PS: Consider reading ubuntuguide.org[/QUOTE]


Thanx for the quick reply.  I'll look at the guide for some help.

-MoLeak

---

### Post by kadymae on 2005-10-18
Heh.  

Let me ask a followup to that question (since I already knew how to do the Opera commandline install)

How do I get it to install in the folder of *my* choosing instead of joining every program on the planet down in /usr/bin?

---

### Post by kadymae on 2005-10-18
Actually, let's forget getting it installed in my folder of preference.  Let's just get it installed.

> 
kadymae@ubuntu:~/downloads$ sudo dpkg -i opera_8.50-20050916.3-shared-qt_en_powerpc.deb
Selecting previously deselected package opera.
(Reading database ... 55503 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.3-shared-qt_en_powerpc.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
 opera depends on libqt3-mt (>= 2:3.0.3); however:
  Package libqt3-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
kadymae@ubuntu:~/downloads$


aroo?  Where from here?

(I'm not a Firefox fan.)

Wait -- just used synaptic to download the missing software bits and reinstall libqt3-mt.

It's installed.  I just now have to go find it and add it to the Applications menu.

---

### Post by MoLeak on 2005-10-18
Ok, something wierd happened.

> Selecting previously deselected package opera.
(Reading database ... 58145 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

So I went into the package manager and installed xlib6 then tried to install Opera again.  Now I get this:

> moleak@ubuntu:~/Desktop$ sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
dpkg: status database area is locked by another process

Now I'm completely stuck.  Did I break something? :confused:   

-MoLeak

---

### Post by mpettitt on 2005-10-18
Looks like you need the QT libraries installed in order to run Opera. The easiest (although not quickest) way to get them is to install the kubuntu-desktop package, since KDE also needs them.
If you are feeling brave, however, you could use Synaptic to find the libqt3-mt package and install it (letting it select all dependencies) and see if that helps.

---

### Post by Qrk on 2005-10-18
If you don't want to install kubuntu-desktop (its big), I'd recommend

sudo apt-get install k3b

A cd burner, it depends on the same things as Opera, and is such a great program you really should have it anyway.  (Gnomebaker works, but K3b really sets the standard) After this you can install opera as you please.

---

### Post by MoLeak on 2005-10-18
[QUOTE=mpettitt]Looks like you need the QT libraries installed in order to run Opera. The easiest (although not quickest) way to get them is to install the kubuntu-desktop package, since KDE also needs them.
If you are feeling brave, however, you could use Synaptic to find the libqt3-mt package and install it (letting it select all dependencies) and see if that helps.[/QUOTE]

One second.  I'll expose my "S" on my chest and go for it.

-MoLeak

---

### Post by MoLeak on 2005-10-18
[QUOTE=Qrk]If you don't want to install kubuntu-desktop (its big), I'd recommend

sudo apt-get install k3b

A cd burner, it depends on the same things as Opera, and is such a great program you really should have it anyway.  (Gnomebaker works, but K3b really sets the standard) After this you can install opera as you please.[/QUOTE]

Big as in how big? 10 meg?  10 gig?

-MoLeak

---

### Post by kadymae on 2005-10-18
Mo-leak

Make sure you close synaptic after downloading and installing related libraries.

---

### Post by NicS on 2005-10-18
yep, if you open synaptic it will let you know that a package is broken, so you probably can find the dependency.
There is probably an esaiest way... but I never install stand-alone package, at least I avoid that to the maximum.
Concerning Opera, errors tells you what to install before it can succeed. Installing single deb file is hard because with apt-get everything is done for you.
You can probably create a local repository in you /etc/sources.list I never done that but I'm sure it's possible.
For Opera again, best way is to get an HowTo on ubuntu wiki which probably exists, or search into this forum.
If you want to install it in your own folder, it's not a .deb that you have to get but .tar.gz containing the binaries, then you can unzip into a directory and run in from there (if Opera provides a binary package take it, it's easy then)

cheers

---

### Post by mpettitt on 2005-10-18
About 300Mb, I seem to remember... Don't actually have it installed though...

(yes, I run KDE, but I _hate_ KsCD which is a dependency of kubuntu-desktop)

---

### Post by Qrk on 2005-10-18
last time I used it, it was 344+MB, but that was the last version. It installs the whole KDE desktop, which is very large. Its like half the default installation over again.

---

### Post by MoLeak on 2005-10-18
[QUOTE=Qrk]last time I used it, it was 344+MB, but that was the last version. It installs the whole KDE desktop, which is very large. Its like half the default installation over again.[/QUOTE]

Thats the size of the desktop package itself?  Pre-install or post install?

Ok, running the qt is done. That seems to allow me to get Opera installed.

> moleak@ubuntu:~/Desktop$ sudo dpkg -i /home/moleak/Desktop/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
Selecting previously deselected package opera.
(Reading database ... 58179 files and directories currently installed.)
Unpacking opera (from .../opera_8.50-20050916.6-shared-qt_en_etch_i386.deb) ...
Setting up opera (8.50-20050916.6) ...

I think that result means it's install right?  Now the big question.  Nothing on the desktop as with XP.  Where did it go?

(these questions have bugged me for years.  I think if I can get through the basics  I might give Linux a real shake out. Can't beat the price. thats for sure)

-MoLeak

---

### Post by mpettitt on 2005-10-18
You need to make the icon yourself.

Right click on the desktop, New Shortcut, and in the command box, put "opera" (no-quotes). Call the shortcut Opera (or whatever you want really) and OK out of the dialog. Click on icon and play with Opera browsing goodness!

---

### Post by MoLeak on 2005-10-18
[QUOTE=mpettitt]You need to make the icon yourself.

Right click on the desktop, New Shortcut, and in the command box, put "opera" (no-quotes). Call the shortcut Opera (or whatever you want really) and OK out of the dialog. Click on icon and play with Opera browsing goodness![/QUOTE]

I don't have New Shortcut as an option from my desktop. (must be a feature I don't have installed yet.) The only thing I can create are folders.  

I can also install something called a **Launcher.**  Same as a shortcut?  If so, I still need  to know where programs install.

-MoLeak

---

### Post by mpettitt on 2005-10-18
Yes, sorry - not running Gnome. Create Launcher, and just type "opera" into the Command Box. It'll sort out the paths itself.

---

### Post by MoLeak on 2005-10-18
[QUOTE=mpettitt]Yes, sorry - not running Gnome. Create Launcher, and just type "opera" into the Command Box. It'll sort out the paths itself.[/QUOTE]

Nahh. It can't be that simple. Can it?   Opera in the command box and BOOM, browser start?  Let's check it out then.

-MoLeak

---

### Post by MoLeak on 2005-10-18
Got Opera running.  

Thank you for all your help.  I hope this thread doesn't go away.  I'm sure I'll reference it from time to time.

-MoLeak

---

### Post by kadymae on 2005-10-18
[QUOTE=MoLeak]I still need  to know where programs install.

-MoLeak[/QUOTE]

Programs install in /usr/bin.

---

### Post by aysiu on 2005-10-18
[QUOTE=MoLeak]Got Opera running.  

Thank you for all your help.  I hope this thread doesn't go away.  I'm sure I'll reference it from time to time.

-MoLeak[/QUOTE] It won't go away, but you probably noticed I changed the title to be what it's really about. Installing programs you use Synaptic or apt-get for (see the second link in my sig). This thread is really about .deb files that exist outside the repositories.

---

### Post by denzilla on 2005-10-18
I got opera installed, but I'm getting this crap. How do I fix this?

---

### Post by migueljacq on 2005-10-19
[QUOTE=denzilla]I got opera installed, but I'm getting this crap. How do I fix this?[/QUOTE]

Looks like your installation of opera failed to load some plugins. I've searched the opera site under [http://www.opera.com/support/service/plugins/index.dml](http://www.opera.com/support/service/plugins/index.dml) but can't find any bug reports for those plugins. Unless someone else here knows of a solution, you might consider filing a bug: [http://www.opera.com/support/bugs/](http://www.opera.com/support/bugs/)

Out of curiousity, did you download opera from their site or from, say, synaptic?

---

### Post by poofyhairguy on 2005-10-19
Best way to install Opera:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by denzilla on 2005-10-19
[QUOTE=migueljacq]Looks like your installation of opera failed to load some plugins. I've searched the opera site under [http://www.opera.com/support/service/plugins/index.dml](http://www.opera.com/support/service/plugins/index.dml) but can't find any bug reports for those plugins. Unless someone else here knows of a solution, you might consider filing a bug: [http://www.opera.com/support/bugs/](http://www.opera.com/support/bugs/)

Out of curiousity, did you download opera from their site or from, say, synaptic?[/QUOTE]

Downloaded Opera from their site. Didn't know it was made avilable through synaptic.

---

### Post by mpettitt on 2005-10-19
From another thread on the forums, you could try doing:
```
cd /usr/lib; ln -s libXm.so.3 libXm.so.2
```

It's a motifwrapper problem whereby it wants an earlier version than is installed by default...

---

### Post by denzilla on 2005-10-19
[QUOTE=mpettitt]From another thread on the forums, you could try doing:
```
cd /usr/lib; ln -s libXm.so.3 libXm.so.2
```

It's a motifwrapper problem whereby it wants an earlier version than is installed by default...[/QUOTE]


Then why didn't the topic starter experience the same problem? We're both using breezy, right?


Tried it, said the file exists.  Dammit! LOL!!!!

---

### Post by mpettitt on 2005-10-19
Different package installed, possibly? I didn't have any problems with the Opera install, but I have kubuntu-desktop installed, which adds the full QT setup, and I've added some other QT packages for development tools.
There are so many possibilities that it could be!

---

### Post by MoLeak on 2005-10-22
[QUOTE=aysiu]It won't go away, but you probably noticed I changed the title to be what it's really about. Installing programs you use Synaptic or apt-get for (see the second link in my sig). This thread is really about .deb files that exist outside the repositories.[/QUOTE]

You're the man!

-MoLeak

---

