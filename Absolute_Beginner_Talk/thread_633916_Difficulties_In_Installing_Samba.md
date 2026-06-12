---
title: "Difficulties In Installing Samba"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Valnorsith on 2007-12-07
I am attempting to set my laptop up so I can access my Windows Vista files from Ubuntu. However, I am encountering some difficulties doing so. Mainly, the Samba download. When I did the simple "new folder, click share, install", it doesn't work. It tells me to download Samba and the other program which I try to do. I click install, the window vanishes for a few moments, then returns again with the exact same message as before.

I then attempted to get Samba via terminal but this is what I got back when I entered the command in: 

xxx@xxx-laptop:~$ sudo apt-get install samba
[sudo] password for xxx:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate

If anyone could please help me since I am new to Ubuntu, it would be greatly appreciated. And I'll give you a cookie if you do. *holds up chocolate chip cookie* Thank you.

---

### Post by PeterJS on 2007-12-07
Looks like your software sources list is setup messed up. The installer does some really dumb things if you don't have an active internet connection when installing, such as assuming all of the software sources should be disabled. To fix this go to System > Administration > Software Sources, and check the check boxes next to the four main repositories (main, restricted, universe, multiverse), close the source selection application and try installing samba again.

EDIT:
And might I suggest looking in to smbfs, it's nice being able to browse smb shares via graphical applications, but being able to tie a remote file system in to your local file system is a whole lot more powerful, think of it like mapping a network drive.

---

### Post by Valnorsith on 2007-12-07
I did as you said and check the 4 that had not been checked. I then went back to install Samba and the other one again and this time, it worked.

Thank you very much and here is the cookie I promised. *hands you big chocolate chip cookie*

---

