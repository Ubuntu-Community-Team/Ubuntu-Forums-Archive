---
title: "Edgy wants my cdrom"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Scarlett on 2007-02-01
I just did a fresh install of Edgy, changed the MBR back to hard drive, with the priority on the same drive grub and Ubuntu are on (I have no idea if that really makes a difference but I saw it somewhere in someone else's topic).  Everything's clean and set to defaults, I haven't fiddled with anything yet.  I go to install alien so I can fight with flash some more and this is the message I get:

sudo apt-get install alien
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpkg-dev html2text libbeecrypt6 librpm4 rpm
Suggested packages:
  lsb-rpm lintian dh-make debian-keyring
The following NEW packages will be installed:
  alien debhelper dpkg-dev html2text libbeecrypt6 librpm4 rpm
0 upgraded, 7 newly installed, 0 to remove and 111 not upgraded.
Need to get 0B/2551kB of archives.
After unpacking 8487kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025.1)'
in the drive '/cdrom/' and press enter

Please help.  I've been tinkering with this for two days now and I'm completely out of ideas.

---

### Post by mizar001 on 2007-02-01
edit as sudo the file /etc/apt/sources.list and comment out the row containing the cd rom reference.

---

### Post by Scarlett on 2007-02-01
When you say comment out, what do you mean?

I added ## to the beginning of each line and now it just aborts after asking me y/n.  Can I just delete those lines?

---

### Post by Scarlett on 2007-02-01
Oops.  I just went back to check to make sure I got all the lines that refer to the cd and the whole thing is gone.  Where'd it go?  Can I get it back?

---

### Post by Scarlett on 2007-02-01
Sorry to triple post, but I guess it's my thread so who's counting.  :-P 

Thanks, that worked!!  Ok, I'm good now.... and off to tackle flash.

---

### Post by mizar001 on 2007-02-01
Nooo! you must add # only to cdrom reference. All other locations must remain enabled (delete the # char before);

---

### Post by mizar001 on 2007-02-01
Any time you make a modification you should do a backup of files. 

You can get edgy fresh sources.list file in this forum or in the support area, if you loose it.

---

### Post by jd65pl on 2007-02-01
If you need a new sources.list then see source-o-matic below it will create a sources list for you which is correct.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by shakma on 2007-03-20
thanks, mizar!  you saved me extended grief.  I just installed a fresh edgy on a new hd after successfully, happily running dapper, then edgy on an old hd for months.  I was stuck with this "insert disc in /cdrom/" error message when trying get nvidia drivers.  I was pulling my hair out.

this totally works.  thanks again.

---

