---
title: "yahoo help"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by pigmelt on 2005-10-12
hello, i just downloaded yahoo instant messenger, when i tried to install i got this error, dpkg: error processing ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
please help. thanks
ps im using breezy.

---

### Post by ubuntumaneh on 2005-10-12
Couple of options:

1)see if you are in the correct directory before trying dpkg

2) use sudo before dpkg -i

---

### Post by pigmelt on 2005-10-12
i downloaded it to a download floder in the home folder. tried using the sudo command, got the same message. dragged the file to the desktop did the install again. do i have to login as root, i'd just assune not to do it that way.

---

### Post by Ampersand on 2005-10-12
try typing 'sudo dpkg -i ymessenger', then press Tab to complete the filename before pressing enter.

---

### Post by ubuntumaneh on 2005-10-12
When you use sudo you are mimicking the root command. Now, you really have to use sudo. In the shell prompt, try this then, just for the sake of test:

$ ls

if you see the .deb package, then you write:

$ sudo dpkg -i ymess {press tab for completion or just type correctly the name of the package}

then it will do.

---

### Post by SilentCacophony on 2005-10-12
Still sounds to me like you may be in the wrong directory. When you open the terminal, it generally starts you at your ~/ (/home/user, where user is your username) directory. Perform an:

ls

and make sure the .deb file is listed. Else use the **cd** command to navigate to where it is.

EDIT -

Or you could use nautilus to copy the file to your home directory.

I suspect that you'll have dependancy problems with it, though.

Have you tried Gaim? It works pretty well.

---

### Post by thespinesplitter on 2005-10-12
do you have anything against GAIM?

---

### Post by pigmelt on 2005-10-13
as a creature of habit, i must say that i am use to using yim. how do you set up a gaim account? the yim is already set up thus a creature of habit. thanks

---

### Post by patrick295767 on 2005-10-13
[QUOTE=thespinesplitter]do you have anything against GAIM?[/QUOTE]

I am agree ... gaim is very very nice program 
(that also works with windows !!)

---

### Post by pigmelt on 2005-10-14
got gaim figure out thanks for the help y messenger is not a concern any more. thanks again

---

### Post by Genican1 on 2006-03-22
Gaim doesn't allow for me to send and recive files via Ymessenger.  I had some trouble installing ymessenger, but finally got it to work, however, the next time I restarted, it would not work.  I tried re-installing, but I also got a message about no such file or directory.  I know the package is there:

me:~$ ls
automatix.log  Incomplete  kubuntu-packages-jriddell-key.gpg  Shared
Desktop        Installs    Multimedia
me:~$ ls Installs
automatix_5.6-2_i386.deb     lincity-ng-data_1.0.1-1_all.deb
lincity-ng_1.0.1-1_i386.deb  ymessenger_1.0.4_1_i386.deb
me:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Password:
dpkg: error processing ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ymessenger_1.0.4_1_i386.deb

Sometimes I get a message saying:

requested operation requires superuser privilege

Any ideas or suggestions?

---

### Post by Princey on 2006-03-22
[QUOTE=Genican1]Gaim doesn't allow for me to send and recive files via Ymessenger.  I had some trouble installing ymessenger, but finally got it to work, however, the next time I restarted, it would not work.  I tried re-installing, but I also got a message about no such file or directory.  I know the package is there:

me:~$ ls
automatix.log  Incomplete  kubuntu-packages-jriddell-key.gpg  Shared
Desktop        Installs    Multimedia
me:~$ ls Installs
automatix_5.6-2_i386.deb     lincity-ng-data_1.0.1-1_all.deb
lincity-ng_1.0.1-1_i386.deb  ymessenger_1.0.4_1_i386.deb
me:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Password:
dpkg: error processing ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ymessenger_1.0.4_1_i386.deb

Sometimes I get a message saying:

requested operation requires superuser privilege

Any ideas or suggestions?[/QUOTE]

From what I'm seeing, you're at the home folder when issuing the sudo dpkg -i command and not in the Installs folder. Do this:
> cd Installs then type > sudo dpkg ymes  press the tab key after ymes then hit the enter key. See if it fails to install this time.

---

