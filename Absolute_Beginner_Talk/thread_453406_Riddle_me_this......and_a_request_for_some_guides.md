---
title: "Riddle me this......and a request for some guides"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-24
i noticed this with edgy and i get the same thing with fiesty.
example - if i want to edit  the /etc/x11/xorg.conf file i open terminal and i type " gksudo gedit /etc/x11/xorg.conf " now when i type this all i get is a blank page :-k
but if i copy and paste the same command line from a thread on the forums or a website into terminal i then get the /etc/x11/xorg.conf file, its the same command line, i even had terminal open and copied and pasted the command in and then typed it exactly as it was in the copied command line and it still didnt work :-k 
very odd.
as for the guides, i would appreciate it if any experienced ubuntu users could point me in the direction of a good set of guides for installing games under linux (games like doom 3 for example) 
and a good set of guides for mounting and burning disc image files (iso's and such like) and for burning and ripping cd's/dvd's  but using command lines rather than gui based prgrams.
cheers

---

### Post by Sparkster185 on 2007-05-24
If you do an ls -l on that file path, does it tell you the file exists?  I'm not 100%, but I believe it's a capital "X", as in /etc/X11/xorg.conf, but I could be wrong.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) is a good guide.  The psychocats one is good, too. 
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Terl on 2007-05-24
It is a capital X - linux is case sensitive!

The directory path is:

```
/etc/X11/xorg.conf
```

If you type something wrong it will assume you mean a new file and hence the blank page.

---

### Post by techno-mole on 2007-05-24
yep its the "x" i should be typing /etc/X11/xorg.conf, im such a plank at times.
cheers for the guides ill give them ago.
cheers

---

### Post by az on 2007-05-24
> **techno-mole said:**
> 

and a good set of guides for mounting and burning disc image files (iso's and such like) and for burning and ripping cd's/dvd's  but using command lines rather than gui based prgrams.
cheers

[http://manual.sidux.com/en/cd-no-gui-burn-en.htm](http://manual.sidux.com/en/cd-no-gui-burn-en.htm)

---

### Post by Nythain on 2007-05-24
[http://www.aircooled.info/global/absolutebeginner-v1-02.pdf](http://www.aircooled.info/global/absolutebeginner-v1-02.pdf)
great for the basics of cli and other stuff

---

### Post by techno-mole on 2007-05-24
cheers for the guides, do any of them cover installing stuff from discs ? like games for instance, i know there are programs like cedega for playing windows based games on a linux machine, but what about games written for linux (or windows games that have been ported) i have a game called descent 3 (which apparently is for linux) but i cant get it to install.
so if anyone has a guide/guides to installing stuff from disc (like games) and one that also covers getting games like doom3 to run under linux, then that will be appreciated aswell.
cheers.

---

### Post by Sparkster185 on 2007-05-24
I've never installed anything (besides Ubuntu itself) from a CD.  What exactly is on the CD?  Is it a tarball, or what?

You might just need to copy the contents of the CD-ROM to a temp directory and then run the typical configure, make, make install commands.

---

### Post by techno-mole on 2007-05-24
well there are alot of files on the disc, but according to the read me i need to do this - see below.

from read me 
" Mount the Descent 3 CD and change the current directory to where
it is mounted. Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
  $ mount /mnt/cdrom
  $ cd /mnt/cdrom
  $ sh setup.sh "
ive tried and it doesnt work, i get a variety of errors depending on what i try.
ill have ago at copying the files over and installing from the hard drive.
cheers

---

### Post by Terl on 2007-05-24
Google is your friend.

If you have a licensed copy of doom3 for windows, id software can hook you up.  Here are all the facts:

[Doom3 on Linux]("http://zerowing.idsoftware.com/linux/doom/")

Another good site for you:  [WineHQ]("http://www.winehq.org/")  Check their apps database.  Great how-to's and loaded with info on how to install, configure and run windows apps using Wine.

---

### Post by Sparkster185 on 2007-05-24
That mount command doesn't look right.  I think the argument to mount needs to be the actual device name (/dev/cdrom, for example).  /mnt is used for devices already mounted, I believe.

---

### Post by Terl on 2007-05-24
> **techno-mole said:**
> well there are alot of files on the disc, but according to the read me i need to do this - see below.

from read me 
" Mount the Descent 3 CD and change the current directory to where
it is mounted. Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
  $ mount /mnt/cdrom
  $ cd /mnt/cdrom
  $ sh setup.sh "
ive tried and it doesnt work, i get a variety of errors depending on what i try.
ill have ago at copying the files over and installing from the hard drive.
cheers

You may have to put sudo in front of the command.

---

### Post by techno-mole on 2007-05-24
i would use wine, but for some reason it just locks up my system, it doesnt matter what commands i use, winecfg etc etc they all have the same effect --try to start winecfg--system locks up--the only way to get out is to push the restart button on the pc case
ive tried 5 or 6 different how to's regarding wine and none of them helped me to get it working.
i will have a look into the doom3 thing though (i have a legit copy of doom3 + expansion pack)
cheers

---

### Post by Terl on 2007-05-24
Do you have a 64bit pc?  I think wine does not like them.  There are directions at their site to get it going though.

---

### Post by techno-mole on 2007-05-24
tried sudo in front of the command i qutoed and i get - command not found 
so if i need to run the setup.sh file from the disc how would i enter the command for it, or what is the command for running setup.sh from the cdrom ?
cheers

---

### Post by techno-mole on 2007-05-24
i do have and amd 64 bit cpu if thats what you mean by 64 bit pc, but im running the 32 bit ubuntu (7.04) ill have alook at the wine website 
cheers.
ok had alook at wine hq, but do i need to install the version of wine for the 64bit ubuntu onto my ubuntu install ? (so install 64bit wine on 32 bit ubuntu ?)
the other thing is that in the instructions for intalling wine it says you need to apt-get some stuff, so i opened terminal and typed in sudo apt-get a32-libs, which is the first thing to install, and whether i use sudo apt-get or just apt-get it comes up with invalid operation ? so what am i doing wrong.
cheers

---

