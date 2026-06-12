---
title: "&quot;not Authenticated"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-02-22
I've seen this a lot lately when installing stuff w/ Add Applications such as monkey bubble.  Is this bad?

---

### Post by codejunkie on 2006-02-22
[QUOTE=inovermyheadd]I've seen this a lot lately when installing stuff w/ Add Applications such as monkey bubble.  Is this bad?[/QUOTE]
it's because you do not have the correct gpg key for a repo in your sources.list file.

---

### Post by inovermyheadd on 2006-02-22
I also get this:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures  were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftp [email]master@ubuntu.com[/email]>


What would the procedure for fixing this problem be?  I appreciate it!

Donald:D

---

### Post by codejunkie on 2006-02-23
[QUOTE=inovermyheadd]I also get this:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures  were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftp [email]master@ubuntu.com[/email]>


What would the procedure for fixing this problem be?  I appreciate it!

Donald:D[/QUOTE]
there's nothing you can really do about it, it's a problem on the repo's end they will eventually fix it.

---

### Post by aysiu on 2006-02-23
See the first link of my sig--the bottom bit (scroll to the end of the page).

---

### Post by inovermyheadd on 2006-02-23
hey, thanks for the reply.

Here is what I got when I tried to follow the last step.

inovermyheadd@wifi-81-51:/etc/apt$ gedit sources.list
inovermyheadd@wifi-81-51:/etc/apt$ sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo apt-get update
cp: `update': specified destination directory does not exist
Try `cp --help' for more information.
inovermyheadd@wifi-81-51:/etc/apt$


I assume I was supposed to save the blank sources.list right?

here is what that looks like

[PHP]deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

## created by arniefreeremoved
[/PHP]

---

### Post by taurus on 2006-02-23
sudo apt-get update 

should be on a seperate line...

---

