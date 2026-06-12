---
title: "Maybe..."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-26
Maybe this box thinks 7.4 is already loaded, so that's why I can't update it...  But it's really running 6.10 still.  Or maybe in all my attempts 7.4 really is loaded, it just didn't tell me...

How do I tell the current version, and how do I verify it is a complete, full, proper load?

Thanks!

---

### Post by eeverson on 2007-04-26
Run this from the terminal to find what version you are running...

cat /etc/issue

What are you running to start the upgrade?

Cheers
Euge

---

### Post by RogerDavis on 2007-04-26
It give me the reply "  Ubuntu 7.04 \n \l  ".

I know I never got an "Upgrade Successful" message, or anything like it.

Is there some way to make sure that I'm really running 7.04, and not just the small file that says 7.04 when you ask about it?

---

### Post by lepz on 2007-04-26
> **RogerDavis said:**
> It give me the reply "  Ubuntu 7.04 \n \l  ".

I know I never got an "Upgrade Successful" message, or anything like it.

Is there some way to make sure that I'm really running 7.04, and not just the small file that says 7.04 when you ask about it?

What you think it's lying to you? ;)

---

### Post by RogerDavis on 2007-04-26
I'm suspicious that in all the screwing around and aborted attempts to upgrade, it only got partially done, and now it thinks it's done and it's not.

---

### Post by bapoumba on 2007-04-26
> **RogerDavis said:**
> I'm suspicious that in all the screwing around and aborted attempts to upgrade, it only got partially done, and now it thinks it's done and it's not.
If you have any doubts:

1- make sure your /etc/apt/sources.list is using feisty repos.
Run **cat /etc/apt/sources.list** in a terminal to see the file.

2-[B] sudo aptitude update
sudo aptitude dist-upgrade[/B]
will finish up the upgrade if necessary.

Edit: to edit the sources.list file:
**sudo nano -B /etc/apt/sources.list**
replace all the non-feisty instances. Save the file with CTRL-O (same name, hit <enter>) and exit nano with CTRL-X.

---

### Post by Sef on 2007-04-26
> sudo nano -B /etc/apt/sources.list

That should be ```
gksudo nano -B /etc/apt/sources.list
```.  If you just use sudo with a graphical interface, you can mess up your system.  From the [RootSudo]("https://help.ubuntu.com/community/RootSudo") page:

>     *

      NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting your username for user.



---

### Post by dstew on 2007-04-26
> NEVER use sudo to start graphical programs.But I thought nano was a text-mode program, not a graphical program. I have used sudo nano lots of times, and it never gives me any problem.

---

### Post by RogerDavis on 2007-04-26
This looks ok?
---------------------------------------
 cat /etc/apt/sources.list

#AUTOMATIX REPOS START
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

#AUTOMATIX REPOS END

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted #Added by software-properties
roger@roger-desktop:~$ 
======================================
I don't see sources?
-------------------------------------------
  GNU nano 2.0.2              File: /etc/apt/sources.list                                  

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.

^G Get Help    ^O WriteOut    ^R Read File   ^Y Prev Page   ^K Cut Text    ^C Cur Pos
^X Exit        ^J Justify     ^W Where Is    ^V Next Page   ^U UnCut Text  ^T To Spell
===========================================================================================
OK, these all say 7.04, but I do see one big difference. lsb_release -a does not show any LSB modules on mine, where that command on eentonigs machine shows several. 

- What's an LSB module, and is it bogus that I have none?
--------------------------------------------------------------------------------
roger@roger-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 7.04
Release: 7.04
Codename: feisty
roger@roger-desktop:~$
=========================================================
Also
--------------------------------
sudo aptitude update

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

roger@roger-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
roger@roger-desktop:~$ 
==================================================================
These checks seem to say to me that something is missing...

---

### Post by bapoumba on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/lsb-release/+bug/36032](https://bugs.launchpad.net/ubuntu/+source/lsb-release/+bug/36032) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **RogerDavis said:**
> 

- What's an LSB module, and is it bogus that I have none?
--------------------------------------------------------------------------------
roger@roger-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 7.04
Release: 7.04
Codename: feisty
roger@roger-desktop:~$
=========================================================

Thats a bug. I get the same output.

> **RogerDavis said:**
> 

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
roger@roger-desktop:~$ 
This is the message you get when you are up to date.

---

### Post by zvacet on 2007-04-26
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


gpg --keyserver hkp://subkeys.pgp.net --recv-keys CC919A31E23C5FC3
 gpg --export --armor CC919A31E23C5FC3  | sudo apt-key add -

---

