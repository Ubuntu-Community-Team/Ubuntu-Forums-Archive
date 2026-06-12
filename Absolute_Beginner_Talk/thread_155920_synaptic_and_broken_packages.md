---
title: "synaptic and broken packages"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by mr.champagne on 2006-04-06
my synaptic says i have a broken package that needs to be fixed but i cant find the package anywhere 
bmp-docklet
i get this error when it loads:
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by aysiu on 2006-04-06
Have you tried this in the terminal? ```
sudo apt-get -f install
```

---

### Post by manicka on 2006-04-06
In synaptic what do you see when you click on the 'Custom' button, then 'broken packages'?

---

### Post by mr.champagne on 2006-04-06
[QUOTE=manicka]In synaptic what do you see when you click on the 'Custom' button, then 'broken packages'?[/QUOTE]
nothing thats the problem synaptic wont find the broken package

sorry to (bump) this i need some more help :)

---

### Post by mr.champagne on 2006-04-07
(bump)help :(

---

### Post by trent dillman on 2006-04-07
sudo apt-get remove bmp-docklet

---

### Post by mr.champagne on 2006-04-09
```
matt@Champagne:~$ sudo apt-get remove bmp-docklet
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.
matt@Champagne:~$

```

---

### Post by trent dillman on 2006-04-09
Have you made any changes to /etc/apt/sources.list ?

---

### Post by mr.champagne on 2006-04-12
no i havent touched any of the sys files

---

### Post by Mustard on 2006-04-12
[QUOTE=mr.champagne]no i havent touched any of the sys files[/QUOTE]
Searching in the repositories I can't even find this bmp-docklet application..

/me keeps searching...

-edit-

Ok, I've searched every repository for every Ubuntu version and bmp-docklet does not exist in the repositories.  From this it would be necessary to deduce that it came from an outside repository.  If you didn't personally change the sources.list then perhaps it was changed by some other application you used.  Did you use the Automatix application to install any of your software?  I would suspect this is the case, because its known to alter the sources.list.

I think you would best reading over this thread and asking there how to uninstall...
[http://www.ubuntuforums.org/showthread.php?t=90797](http://www.ubuntuforums.org/showthread.php?t=90797)

Basically you need to find out what repositories where added to your sources.list to install all the beep-media player packages, so that you can reverse the process.

---

### Post by mr.champagne on 2006-04-18
```
matt@Champagne:~$ sudo apt-get remove beep-media-player beep-media-player-dev beep-media-player-docklet
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.

```



this is a head scratcher for me

---

### Post by mr.champagne on 2006-04-19
(bump)

---

### Post by Mustard on 2006-04-19
The only thing I can think of is that somehow it came from an outside repository, and now that repository has been disabled/deleted from the sources.list, so it's unable to find the package anymore to reinstall it.

---

### Post by BLZPLZ on 2006-04-21
I am another user of the same computer that mr.champagne is on.
I modified sources.list to enable extra repositories so i could get flash to download on my computer.  Obviously something went wrong. I tried using source-o-matic, and reverting back to normal repositories but still, I can't uninstall beep media player

---

### Post by BLZPLZ on 2006-04-21
I keep getting the bmp-docklet error no matter what i try.

Could someone help?  Being able to install and uninstall files is prreeeetty handy. :D

---

### Post by BLZPLZ on 2006-04-21
I also tried downloading the bmp-docklet package and installing it, after using the repositories that source-o-matic gave me.

same error.

---

### Post by Mustard on 2006-04-21
What sources have you added?
So you tried to install it using dpkg?
Did you apt-get update and try to install it through synaptic or apt-get?

These descriptions you are giving are very sketchy on details.  Please explain in more detail what you do at each step and paste the commands and the output of the commands you have tried.

---

### Post by BLZPLZ on 2006-04-22
Here is my source.list file. I got it from source-o-matic.  I ran apt-get update after saving and closing the gedit file.

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
***these are my attempts to install the bmp-docklet .deb package I downloaded using dpkg***





matt@Champagne:~$ dpkg --update-avail bmp-docklet-1.3
dpkg: bulk available update requires write access to dpkg status area


matt@Champagne:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 bmp-docklet          <insert up to 60 chars description>

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 amsn                 An MSN messenger written in tcl

matt@Champagne:~$ dpkg -i bmp-docklet-1.3
dpkg: requested operation requires superuser privilege
matt@Champagne:~$ dpkg -c
dpkg-deb: --contents takes exactly one argument

matt@Champagne:~$ dpkg -i bmp-docklet-1.3
dpkg: requested operation requires superuser privilege


How do I change my permissions?  Sorry about noobing it up, I've only had ubuntu for a month, and before this, I've never touched a system running linux before that...So at this point I'm still trying to learn to the best of my abilites.

---

### Post by BLZPLZ on 2006-04-22
Also, tried to install using synaptic package manager

error message:

E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by BLZPLZ on 2006-04-22
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

this is what happens when I go:
edit > reload package information

---

### Post by Mustard on 2006-04-22
the dpkg command would need to be used with 'sudo' in front of it to execute it as a superuser.

An example from one of the commands you tried above...

```
sudo dpkg -i bmp-docklet-1.3
```

This will ask you to enter a password.  You enter your user password.  This all assumes that your current user account is set up with sudo privileges.

---

### Post by BLZPLZ on 2006-04-22
> dpkg-split: error reading bmp-docklet-1.3: Is a directory
dpkg: error processing bmp-docklet-1.3 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 bmp-docklet-1.3



hmmm any ideas?

---

### Post by Princey on 2006-04-22
[QUOTE=BLZPLZ]hmmm any ideas?[/QUOTE]

The problem is coming from beep media player. I'm not sure what methods were used to install it, but why don't you try using Automatix. Not only does it install it, but it adds extra sources to your sources.list. That should add the extra repositories needed to fix your problem. After that, you can just type > sudo apt-get remove beep media player if you don't want it. The important thing is that you'll be fixing the dependency problem.

---

### Post by BLZPLZ on 2006-04-22
I got beep media player from Automatix.  I tried re-installing Automatix, but I got the same bmp-docklet error.  This can only lead me to assume that I need to install the bmp-docklet package itself to fix this problem.  Exactly how I need to do that is what is screwing me up.

---

### Post by Princey on 2006-04-22
[QUOTE=BLZPLZ]I got beep media player from Automatix.  I tried re-installing Automatix, but I got the same bmp-docklet error.  This can only lead me to assume that I need to install the bmp-docklet package itself to fix this problem.  Exactly how I need to do that is what is screwing me up.[/QUOTE]

Did you try > sudo apt-get remove beep media player

---

### Post by Mustard on 2006-04-22
[QUOTE=BLZPLZ]hmmm any ideas?[/QUOTE]

Well the error message 'Is a directory' seems to be the most solid clue in the error message.  What this means exactly I'm not sure, but I could take a guess, with some more information.

What folder is this .deb package in?
What was the command you entered that gave that error message?
Did you extract this .deb package before attempting to install?
(I just ask this because its not necessary to extract the package, so I want to make sure thats not what you are doing.)

Also and this is probably more important than the other questions.  I didn't give you the right syntax for the command above. When using dpkg -i you are installing a .deb package locally, so the the full file name needs to be used when installing...

```
sudo dpkg -i bmp-docklet-1.3.deb
#note that I have added .deb on the end
```

It seems to be saying that you are not referring to a file in the command, but are referring to a directory.  This is a bit strange really, as I would expect it to simply say that it can't find the file.  Anyway, a more elaborate description would help me to know exactly what you are doing.  Not including the command you entered to get the output that you did means I have only half the story to work with.

You can tell the current working directory you are in with this command..

```
pwd
```

You can find the contents of the current directory with this command..

```
ls -al
```

---

### Post by BLZPLZ on 2006-04-23
matt@Champagne:~$ cd /home/matt/Desktop
matt@Champagne:~/Desktop$ sudo dpkg -i bmp-docklet
dpkg: error processing bmp-docklet (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bmp-docklet
matt@Champagne:~/Desktop$ sudo dpkg -i bmp-docklet.deb
Selecting previously deselected package bmp-docklet-1.3.
(Reading database ... 88100 files and directories currently installed.)
Unpacking bmp-docklet-1.3 (from bmp-docklet.deb) ...
dpkg: error processing bmp-docklet.deb (--install):
 trying to overwrite `/usr/lib/bmp/General/libdocklet.a', which is also in package bmp-docklet
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bmp-docklet.deb

---

### Post by Mustard on 2006-04-23
[QUOTE=BLZPLZ]matt@Champagne:~$ cd /home/matt/Desktop
matt@Champagne:~/Desktop$ sudo dpkg -i bmp-docklet
dpkg: error processing bmp-docklet (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bmp-docklet
matt@Champagne:~/Desktop$ sudo dpkg -i bmp-docklet.deb
Selecting previously deselected package bmp-docklet-1.3.
(Reading database ... 88100 files and directories currently installed.)
Unpacking bmp-docklet-1.3 (from bmp-docklet.deb) ...
dpkg: error processing bmp-docklet.deb (--install):
 trying to overwrite `/usr/lib/bmp/General/libdocklet.a', which is also in package bmp-docklet
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bmp-docklet.deb[/QUOTE]

It just gets worse every time doesn't it. :)

---

### Post by Princey on 2006-04-23
[QUOTE=BLZPLZ]matt@Champagne:~$ cd /home/matt/Desktop
matt@Champagne:~/Desktop$ sudo dpkg -i bmp-docklet
dpkg: error processing bmp-docklet (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bmp-docklet
matt@Champagne:~/Desktop$ sudo dpkg -i bmp-docklet.deb
Selecting previously deselected package bmp-docklet-1.3.
(Reading database ... 88100 files and directories currently installed.)
Unpacking bmp-docklet-1.3 (from bmp-docklet.deb) ...
dpkg: error processing bmp-docklet.deb (--install):
 trying to overwrite `/usr/lib/bmp/General/libdocklet.a', which is also in package bmp-docklet
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bmp-docklet.deb[/QUOTE]

I had a similar issue a month or so aback while updating to the latest release of amule. Ran into that broken pipe saga that even synaptic or apt-get couldn't solve. After much reading, I found a 'dirty' way to remove the app by force deleting the directory. From what I'm reading in the above quote from you, it seems that bmp-docklet.deb is referenced in the broken pip lib docklet, so we need to force it to be deleted. Type this at the terminal: > sudo rm -rf /usr/lib/bmp/General/liibdocklet.a and press enter, followed by > sudo ldconfig Just to be sure, type after > whereis bmp-docklet and press enter. If it only says bmp-docklet, then it's removed. If it lists locations such as /usr/local/ use the above command > sudo rm -rf /directory path where directory path is the path to which the other listings to bmp-libdocklet point to. Run > sudo apt-get update when done and let us know if you get the dependency errors that you first got when you posted your problem.

---

### Post by BLZPLZ on 2006-04-23
matt@Champagne:~$ sudo rm -rf /usr/lib/bmp/General/libdocklet.a
matt@Champagne:~$ sudo ldconfig
matt@Champagne:~$ whereis bmp-docklet
bmp-docklet:
matt@Champagne:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/multiverse Sources
Fetched 5B in 1s (4B/s)
Reading package lists... Done


does this look right?  ...It didn't seem like those commands were doing anything; as you can see there's almost no output after the first 3...

---

### Post by Princey on 2006-04-23
Yes, it's right. Now, to verify that the problem is solved, type this > sudo apt-get upgrade It should run and update if there're any updates. If not, it should return at the end 0 packages update, 0 installed, 0 removed.

---

### Post by BLZPLZ on 2006-04-23
](*,) 
 
matt@Champagne:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.

---

### Post by Princey on 2006-04-23
[QUOTE=BLZPLZ]](*,) 
 
matt@Champagne:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.[/QUOTE]

Ok, so we've got half the problem solved. What I need to know now is which program needs bmp-docklet to run. Knowing which, we can safely remove the offending package. Is it beep media player?

---

### Post by BLZPLZ on 2006-04-23
yep, it's beep media player, I've tried removing it before and I get the same error message saying that bmp-docklet needs to be installed

---

### Post by Princey on 2006-04-23
[QUOTE=BLZPLZ]yep, it's beep media player, I've tried removing it before and I get the same error message saying that bmp-docklet needs to be installed[/QUOTE]

ok...let's try this. I may be wrong with the actual name but you can always substitute what I have with the actual name: Code: > whereis beep media player as I said, the name may be wrong but you can substitute with the actual name. When it lists the location, type the following: Code: > sudo rm -rf /path of program where you substitute 'path of program' with the actual patch. Repeat for each location listed for beep media player. That should force it out of the system.

---

### Post by BLZPLZ on 2006-04-23
```
matt@Champagne:~$ whereis beep media player
beep: /usr/share/man/man3/beep.3blt.gz
media:
player:
matt@Champagne:~$

```

would it be easyer to format and reinstall ubuntu

---

### Post by Princey on 2006-04-24
[QUOTE=BLZPLZ]```
matt@Champagne:~$ whereis beep media player
beep: /usr/share/man/man3/beep.3blt.gz
media:
player:
matt@Champagne:~$

```

would it be easyer to format and reinstall ubuntu[/QUOTE]

You don't have to. I did a check on my system and beep media player is installed. Here's the output of whatis on my system: > whereis beep-media-player
beep-media-player: /usr/bin/beep-media-player /usr/bin/X11/beep-media-player /usr/share/man/man1/beep-media-player.1.gz

That means it's installed in 3 different directories so you'd have to input the following commands one line at a time pressing enter after each: > sudo rm -rf /usr/bin/beep-media-player
sudo rm -rf /usr/binX11/beep-media-player
sudo rm -rf /usr/share/man/man1/beep-media-player.1.gz When done, type the following > sudo ldconfig

Now, try > sudo apt-get update followed by > sudo apt-get upgrade There should be no reference to bmp-docklet now.

---

### Post by Mustard on 2006-04-26
[QUOTE=BLZPLZ]```
matt@Champagne:~$ whereis beep media player
beep: /usr/share/man/man3/beep.3blt.gz
media:
player:
matt@Champagne:~$

```

would it be easyer to format and reinstall ubuntu[/QUOTE]

It's not really necessary, but I know when I get in a major tangle I tend to do that.  It depends on how much customisation and setting up you've done with this installation. If you've spent many hours getting it to a certain point, you might prefer to attempt to fix the problem manually.  If you've just recently installed, then a format and reinstall is a pretty easy option.

---

### Post by Mustard on 2006-04-26
Might be too late now, but you might like to read over this thread which popped up recently. :)
[http://www.ubuntuforums.org/showthread.php?t=162306](http://www.ubuntuforums.org/showthread.php?t=162306)

---

