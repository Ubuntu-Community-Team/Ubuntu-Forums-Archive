---
title: "$gksudo gedit /etc/apt/sources.list"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by nehc on 2007-04-24
I copy and paste this command in the termial
$gksudo gedit /etc/apt/sources.list
a new window open with this 
[HTML]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
[/HTML]

why i have this error?

---

### Post by Belyel on 2007-04-24
I don't see any errors there.  That is the sources.list file.  It has a listing of the repositories that you access for software.  Anything that has a # in front of it is a comment, there for your reference.  Anything with a deb or deb-src in front is a repository.

---

### Post by Rui Pais on 2007-04-24
> **nehc said:**
> I copy and paste this command in the termial
$gksudo gedit /etc/apt/sources.list
a new window open with this 
[HTML]...
sniped
...[/HTML]

why i have this error?
what error?

if you mean that it fail to save any changes, thats because you are overpassing the gksudo command with the sigh $ in front of it.
The correct way is:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by steve.horsley on 2007-04-24
As the others have said, there doesn't seem to be an error here. The command you entered opened an editor (gedit) to edit the file /etc/apt/sources.list. And the gksudo at the front asked for the perermission to write the file as well as just view it.

So you are looking at a text configuration file in an editor (like notepad). Lines beginning with a "#" don't do anything - they are comments. The other lines gove information about the different software repositories that Ubuntu can try and get software from. 

Since you are so unsure what you are doing with this file, can I suggest that you don't edit and change it until you have discussed what to do and why with people on this forum? A mistake editing this file could cause problems that prevent you installing any more software or updates. And beginners shouldn't really have to edit this file - you can probably do what you need to in a GUI which may feel nore comfortable to you.

---

### Post by aysiu on 2007-04-24
**Here's a translation for you**
*gksudo* - with administrative permissions, execute the following graphical application
*gedit* - yup, this is the graphical application I want to open... the text editor Gedit
*/etc/apt/sources.list* - the file called *sources.list* inside the *apt* directory inside the *etc* directory.

---

