---
title: "yahoo"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by firebird45331 on 2006-05-28
Ok so I thought I'd run wine with yahoo messenger 7.5 but then it says it needs files from IE 5.0.  I don't wanna mess with that.  Any version of Yahoo that runs with ubuntu?  I thought maybe the debian thing would but it's not.  this is cool though I'm learning.  about the only way I learn is to break stuff.

---

### Post by jgoguen on 2006-05-28
Gaim handles the Yahoo! network.  It's in the default install of Ubuntu, in Applications -> Internet -> Gaim Instant Messenger.

---

### Post by richbarna on 2006-05-28
Try this :-
[How to install yahoo messenger for Gnome]("http://ubuntuforums.org/showthread.php?t=81895")

---

### Post by firebird45331 on 2006-05-28
ok just did that and it's saying it can't access the archive

---

### Post by richbarna on 2006-05-28
[QUOTE=firebird45331]ok just did that and it's saying it can't access the archive[/QUOTE]
Ok, be more specific, "what" says "what" can't acces "what" archive ?
Maybe you mean :-
> sudo apt-get install libssl0.9.6
Try version 0.9.7, I've got 0.9.8 but I'm using Dapper (I don't think that makes a difference).
> sudo apt-get install libssl0.9.7

---

### Post by firebird45331 on 2006-05-28
this is what I'm doing

monte@cpe-24-166-223-238:~$  sudo dpkg -i /home/monte/desktop/ymessenger_1.0.4_1_i386.deb
Password:
dpkg: error processing /home/monte/desktop/ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/monte/desktop/ymessenger_1.0.4_1_i386.deb
monte@cpe-24-166-223-238:~$

---

### Post by richbarna on 2006-05-28
Ok, try this :-
Copy the deb file into your home folder, then in terminal type :-
su
password
cd /home/monte/ (you should be at root@cpe-24-166-223-238: /home/monte #)
dpkg -i ymessenger_1.0.4_1_i386.deb

i've had problems with .deb's on the desktop before (don't ask me why),
so I always put them in the home folder and install them as root.

---

### Post by firebird45331 on 2006-05-28
ok I do that, but the terminal  says authentication failure when I type in my password

---

### Post by richbarna on 2006-05-28
Did you use your root password or your user password?

---

### Post by firebird45331 on 2006-05-28
um what's my root password? I'm completely illiterate here.  I used my user password there before and it worked just not now.

---

### Post by richbarna on 2006-05-28
ok, you can create a root password, or change it like this :-
> sudo passwd root

---

### Post by firebird45331 on 2006-05-28
slowly but surely I'm getting somewhere.  I have to be going, but here's what it said

dpkg: requested operation requires superuser privilege
monte@cpe-24-166-223-238:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Password:
Selecting previously deselected package ymessenger.
(Reading database ... 61814 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

---

### Post by firebird45331 on 2006-05-28
I think I might have done something right I don't remember the command but it came up as having a broken package and I typed sudo apt-install -f or something like that and it fixed the broken package.  on the terminal it said ymessenger installed

---

### Post by Engnome on 2006-05-28
[QUOTE=firebird45331]slowly but surely I'm getting somewhere.  I have to be going, but here's what it said

dpkg: requested operation requires superuser privilege
monte@cpe-24-166-223-238:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Password:
Selecting previously deselected package ymessenger.
(Reading database ... 61814 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger[/QUOTE]


Grats youre in dependency hell. The line that says:

 ymessenger depends on libgtk1.2

says you need that library.

Try:

sudo apt-get install libgdk-pixbuf2 libglib1.2 libgtk1.2 xlibs

and then try dpkg again.

---

### Post by firebird45331 on 2006-05-28
this is what it's saying now

monte@cpe-24-166-223-238:~$ sudo apt-get install libgdk-pixbuf2 libglib1.2 libgtk1.2 xlibs
Reading package lists... Done
Building dependency tree... Done
libgdk-pixbuf2 is already the newest version.
libglib1.2 is already the newest version.
libgtk1.2 is already the newest version.
xlibs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
monte@cpe-24-166-223-238:~$ cd /home/monte/
monte@cpe-24-166-223-238:~$ dpkg -i ymessenger_1.0.4_1_i386.deb
dpkg: requested operation requires superuser privilege
monte@cpe-24-166-223-238:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 61950 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
Setting up ymessenger (1.0.4_1) ...

---

### Post by Engnome on 2006-05-28
[QUOTE=firebird45331]this is what it's saying now

monte@cpe-24-166-223-238:~$ sudo apt-get install libgdk-pixbuf2 libglib1.2 libgtk1.2 xlibs
Reading package lists... Done
Building dependency tree... Done
libgdk-pixbuf2 is already the newest version.
libglib1.2 is already the newest version.
libgtk1.2 is already the newest version.
xlibs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
monte@cpe-24-166-223-238:~$ cd /home/monte/
monte@cpe-24-166-223-238:~$ dpkg -i ymessenger_1.0.4_1_i386.deb
dpkg: requested operation requires superuser privilege
monte@cpe-24-166-223-238:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 61950 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
Setting up ymessenger (1.0.4_1) ...[/QUOTE]

you have to type sudo before dpkg.

more info about sudo: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Edit ops my bad you tried it secondly...

It seems like it installed though. You dont have it in the menus? Do you have debian menu?

---

### Post by firebird45331 on 2006-05-28
before I even bother does this version of yahoo even have webcam support?

---

