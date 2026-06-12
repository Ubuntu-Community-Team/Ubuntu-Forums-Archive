---
title: "[SOLVED] Add/Remove and synaptics manager"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-19
whenever i try to run either one of these it just locks up for hours, also sometimes when i try to bring it back from the screensaver the screen stays black but the mouse comes back and there is nothing i can do but power off manually. Any ideas???

---

### Post by Tyke91 on 2008-03-19
no clue... are you able to apt-get install things?

also, system specs plez

---

### Post by N1N31NCHN41L5 on 2008-03-19
dell lattitude c400 intel celeron processor 1.2g 256mb mem xubuntu 7.10 Gutsy Gibbon

---

### Post by N1N31NCHN41L5 on 2008-03-19
i think so but nothing i need to get right now - i think

---

### Post by mcduck on 2008-03-19
Try starting Synaptic from a terminal and see if you get any error messages..

---

### Post by N1N31NCHN41L5 on 2008-03-19
how do i start it in a terminal, I only was born again 3 weeks ago - still a Linux newbie

---

### Post by Captainm on 2008-03-19
```
gksudo synaptic
```

---

### Post by N1N31NCHN41L5 on 2008-03-19
Sweet - that workde - ok sudo is suoer user - synaptic is synaptics manager, what is gk??? and how do i do this for add/remove?

---

### Post by mcduck on 2008-03-19
> **N1N31NCHN41L5 said:**
> Sweet - that workde - ok sudo is suoer user - synaptic is synaptics manager, what is gk??? and how do i do this for add/remove?

'gksudo' does the same thing 'sudo' does, but is made for use with graphical programs. (you should _never_use 'sudo with GUI apps, while it works for some cases in others it might mess the ownerships of setting files in your hoem directory, making you unable to log in any more).

Gksudo also has a graphical dialog for inputting the password, so you don't need a terminal for it. This makes it possible to start apps as root using desktop menus and launchers.

Anyway, if I remember right the add/remove-thing is actually called gnome-app-install, so you can start it from a terminal with "gksudo gnome-app-install"

---

### Post by N1N31NCHN41L5 on 2008-03-19
thanks - what all makes a graphical program so i know when 2 use it

---

### Post by undertakingyou on 2008-03-19
> **N1N31NCHN41L5 said:**
> thanks - what all makes a graphical program so i know when 2 use it

Rule of thumb, If it has pretty picture and uses the mouse to 'click' through commands it is graphical or 'GUI'.  If it is text based and/or just has keyboard input in a terminal it as Command line based or 'CLI'

---

### Post by N1N31NCHN41L5 on 2008-03-19
tanks a lot - now all i need is the damn add remove to work it locks up and freezes either during loadup or it says its out of date and lock up during update

---

### Post by undertakingyou on 2008-03-19
I am curious, I assume that you are hooked up to the internet when you are running the programs.  What does your sources list look like?  Can you open a terminal and type ```
cat /etc/apt/sources.list
``` and post the output here?

---

### Post by N1N31NCHN41L5 on 2008-03-19
sure thing - here ya are:

josh@xubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by undertakingyou on 2008-03-19
ok, the first thing that I see is that it wants to look at your original installation CD to get packages.  I would remove that.  Also you may want to enable the backport repos.  So run the following in a terminal ```
gksudo gedit /etc/apt/sources.list
``` remove the lines at the begining so that it starts with > # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to then if you want to enable the backports remove the hash (#) from the following lines > # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverseAfter that do the following in a terminal```
sudo aptitude update
sudo aptitude safe-upgrade
``` and then try to open the add/remove program.

---

### Post by AndyCooll on 2008-03-19
Part of the problem is that the second line indicates that it is looking for the Xubuntu CD-ROM.

Type into the command line:
```
gksudo gedit /etc/apt/sources.list
```
And place a # at the beginning of the third line (the one beginning deb cdrom ....)
Save the file and then type:
```
sudo apt-get update
```
Then try using Add/Remove or Synaptic again.

:cool:

---

### Post by undertakingyou on 2008-03-19
Also I just have to say, what a cryptic way to say Nine Inch Nails.  Took me ten minutes to figure that out.  :)

---

### Post by N1N31NCHN41L5 on 2008-03-19
this is what i got - nothing:

josh@xubuntu:~$ 
josh@xubuntu:~$ gksudo gedit /etc/apt/sources.list
josh@xubuntu:~$ 


thats how he spelled it on the last remixed cd :guitar:

---

### Post by undertakingyou on 2008-03-19
Bummer.  Try ```
sudo gedit /etc/apt/sources.list
``` 
I thought gksudo would work but maybe I am wrong :]

---

### Post by N1N31NCHN41L5 on 2008-03-19
heres that result:


josh@xubuntu:~$ 
josh@xubuntu:~$ gksudo gedit /etc/apt/sources.list
josh@xubuntu:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found

---

### Post by undertakingyou on 2008-03-19
What?  No gedit?  that is not natural.  Do you have gnome installed?  Anyways there is another way.  ```
sudo vim /etc/apt/sources.list
```once in there just use the delete key to get rid of the stuff we don't want and then type in ```
:wq
```  Then do the rest of the list.

---

### Post by N1N31NCHN41L5 on 2008-03-19
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

---

### Post by N1N31NCHN41L5 on 2008-03-19
Now i get this:

josh@xubuntu:~$ cat /etc/apt/source.list
cat: /etc/apt/source.list: No such file or directory
josh@xubuntu:~$

---

### Post by mcduck on 2008-03-19
> **N1N31NCHN41L5 said:**
> thanks - what all makes a graphical program so i know when 2 use it

Anything that is not strictly command-line based, every program that has it's own window and graphical user interface.

---

### Post by forrestcupp on 2008-03-19
He's using Xubuntu.  What is the text editor that comes with Xubuntu?  That is what he needs to use to edit sources.list

---

### Post by forestpixie on 2008-03-19
mousepad

Edit - a bit terse - what I should have said was change gedit to mousepad

```
gksudo mousepad /etc/apt/sources.list
```

---

### Post by N1N31NCHN41L5 on 2008-03-20
# 
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



ok - thats what i get when i do this:
josh@xubuntu:~$ gksudo mousepad /etc/apt/sources.list

---

### Post by AndyCooll on 2008-03-20
You then need to place # in front of line 4, it currently looks like this:

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

It should look like this:

#deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

All lines with a # in front of them are ignored from a command/instruction point of view.
Anyway, save the modification and type:
```
sudo apt-get update
```
You should then be ready to go, and Add/Remove and Synaptic should now function properly.

:cool:

---

### Post by N1N31NCHN41L5 on 2008-03-20
the end of the last post and what i got after

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
wq!
sudo apt-get update

---

### Post by N1N31NCHN41L5 on 2008-03-20
what do i do to fix this


E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Wed Mar 19 22:53:54 2008
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: xubuntu
        process ID: 10733
While opening file "/etc/apt/sources.list"
             dated: Thu Mar 20 23:40:45 2008
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.
"/etc/apt/sources.list" 59L, 3148C
Press ENTER or type command to continue

---

### Post by forestpixie on 2008-03-20
if you've actually got 
> wq!
at the end of your sources list - you shouldn't have so edit it again

as far as the E325 - never seen that before - but reading it I would do as it says and delete the swap file 

```
sudo rm /etc/apt/.sources.list.swp
```

then do sudo apt-get update

---

### Post by N1N31NCHN41L5 on 2008-03-20
ty

---

