---
title: "The Most Basic of Questions (Installing Downloaded Files)"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by twoseids on 2005-06-04
Hey everyone,

Long-time Windows user (I'm no hacker, but I'm very comfortable with the computer), but brand spanking new on Linux.  Using Hoary 5.04.

I'm trying to install some software but can't even figure out how!  Two examples:

1.  [COLOR=Blue]Firefox update[/COLOR]:  I have downloaded the update (the file is called firefox-installer), but how do I install it?
2.  [COLOR=Blue]Skype[/COLOR]:  I downloaded a .deb file, and tried to follow the instruction in the Ubuntu guide (sudo dpkg -i skype_1.1.0.13-1_i386.deb) but when I did that, got this error message:  [COLOR=Red]dpkg:  status database area is locked by another process[/COLOR]

Can someone please point me to a step-by-step idiot's guide to installing a new program?  Thanks!

---

### Post by bored2k on 2005-06-04
1. Firefox 1.0.4 install (two methods: choose B):
a)
I. Applications > system > terminal : type chmod +x nameofFirefoxinstaller (the file needs to be in your home)
II. ./applicationName
b) Forget about the installer, use [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) . After that is done, in synaptic package manager perform an upgrade.

* Method 1 will not overwrite your current firefox.

2. It is locked because you have synaptic package manager open OR another process using apt-get. Apt is jealous. Only one relationship at a time ;).

---

### Post by twoseids on 2005-06-04
I do have the update manager downloading like 360 files...so maybe that's why I am having problem #2.

For that matter, I wonder if Firefox 1.0.4 is one of those 360 files?  And while I'm on the topic of those files, are they all self-installing like in Windows?

---

### Post by bored2k on 2005-06-04
[QUOTE=twoseids]I do have the update manager downloading like 360 files...so maybe that's why I am having problem #2.

For that matter, I wonder if Firefox 1.0.4 is one of those 360 files?  And while I'm on the topic of those files, are they all self-installing like in Windows?[/QUOTE]
 Self-Installing ? Yes. Like Windows ? Definitely not. Is there such thing in Windows ? Don't you have to read a thick EULA and click next and finish a gazillion times ?

Anyway, yes self installing. If you followed the ubuntuguide.org repositories, you will get the latest firefox.

---

### Post by mtron on 2005-06-04
hi twoseids, Welcome to Ubuntu! 

First of all some quick basics about installing:

the best method to install software is using the Ubuntu Software installer called "Synaptic Package Manager". Find it under System - Administration.

It is very easy to use click on the search button, type in the package name and apply. the rest is done by Synaptic. Linux does not require a reboot after installing new software (exept you install a new kernel). If you use the extra repositories, as described in the [ubuntuguide](http://ubuntuguide.org/index.html#extrarepositories) you can choose between thousands of packages pre-compiled for your ubuntu.

In case your wanted package is not available, download the source (usually from the project homepage) which comes in an archive (*.tgz ect), unpack it and read the "Install" or Readme file, but to compile a package, the most common steps are:

Open a terminal (the $ in front of some commands indicates that these should be typed in a terminal window)
cd to the folder where you unpacked the source
$ ./configure
$ make
$ sudo make install

Some Programms also come with installer files (*.bin or just executeables). after download check that the file permissions are set to executeable (right click on the file - Properties - Permissions Tab, check "execute") and then open a terminal and type "sudo packagename.bin" or "sudo ./packagename" it the installer is a script 

For the firefox update: 
i suggest using the ubuntu backport instead the installer, because it integrates better with the rest of the OS and comes in a deb format (deb is the debian package format), to add this backports open a terminal and type

$ sudo gedit /etc/apt/sources.list

add the following lines at the end of the file
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

save it, close the editor and back in terminal type
$sudo apt-get update

and
$sudo apt-get upgrade
or
$sudo apt-get dist-upgrade

the apt-get programm does more or less the same as the Synaptic package manager. to see an explanation of this apt-get commands, have a look [here](http://www.ubuntuforums.org/showthread.php?p=104267#post104267) 

The error "dpkg: status database area is locked by another process" means that you had Synaptic open during you used the apt-get command. Close Synaptic and it will work.

Good Luck!

---

### Post by mtron on 2005-06-04
man you guys are fast, when i started writing there wars no answer and now... wow.

ok, i was too slow. Time to get some sleep. was a nice party yesterday   O:)

---

### Post by twoseids on 2005-06-04
Thanks bored2k, I've done that repositories thing, so we'll see how it goes.

mtron - thanks for that great reply.  It went nicely with bored's reply, and has a couple other tidbits that I'm sure I'll come back to once I try downloading and installing something else.  So don't consider it a waste of time - I appreciate it!

---

### Post by Seti on 2005-06-04
[QUOTE=bored2k] Is there such thing in Windows ? Don't you have to read a thick EULA and click next and finish a gazillion times ?
[/QUOTE]
Yes there is such a thing in windows, its called a virus. And you don't even need to click to accept a big bad EULA.

(sorry, just couldn't resist)

---

### Post by bored2k on 2005-06-04
[QUOTE=Seti]Yes there is such a thing in windows, its called a virus. And you don't even need to click to accept a big bad EULA.

(sorry, just couldn't resist)[/QUOTE]
 LoL my bad. Forgot about those LOL.
[IMG]http://img32.echo.cx/img32/4682/insertdisk8ls.jpg[/IMG]

---

### Post by Jenda on 2005-06-04
Haha!!! that one had me rroollinnn, bored2k! HAha...

---

### Post by twoseids on 2005-06-04
Okay, I've gone through the Synaptics Package Manager and installed a bunch of stuff.  Now how do I get it to show up somewhere - anywhere?  I can see that my Firefox is now upgraded, so that worked.  But I installed, for example, Skype, and it seemed to install successfully, but now where is it?  And where are the games I installed?  They're not under Applications -- Games.

Where do all the installed files go?  Dang, I feel like an idiot!  Linux has a bit of a learning curve but I want to stick it out.

---

### Post by bored2k on 2005-06-04
If you install certain packages and they dont show up in the menu:
1. You need to refresh the menus (log out/in or killall gnome-panel) 
or
2. Install menu menu-xdg package. This will make a Debian menu show up with everything.

If you still do not see skype, you could still run it typing skype on a terminal and **creating** your own menu entry for it: [http://ubuntuforums.org/showthread.php?t=38183&highlight=smeg](http://ubuntuforums.org/showthread.php?t=38183&highlight=smeg)

To install smeg easily: Applications > system tools > Root terminal (input your password) then do this:
```
wget http://dev.realistanew.com/smeg/installsmeg
chmod +x installsmeg
./installsmeg
```
After that is done (internet connection eeded) you can find the Smeg Menu Editor in Apps > Sys tools.

Installed files ? usually in /usr/lib . They are hidden from you because you do not need to touch them nor get a cluttered file manager (how many times have you not messed up .exe's ;)?).

Ubuntu Linux is not that hard, its just that you want to do stuff a gazillion stuff at once :D.

P.S. - Loving your avatar

---

