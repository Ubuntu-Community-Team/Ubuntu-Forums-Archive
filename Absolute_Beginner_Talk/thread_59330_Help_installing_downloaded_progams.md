---
title: "Help installing downloaded progams"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-23
Hi guys i want to know how to install download progams i know how to install progams in synaptic package manger but i dont know how to install progam i have download EG i have download winrar for linuxs but dontknow how to install it is there any steps u can tech me thanks

---

### Post by izmaelis on 2005-08-23
```
dpkg -i package.of.a.program.deb
```
if you downloaded package for Debian type systems.
```
./configure
make
make install

```if you trying to install it from source.

---

### Post by Stormy Eyes on 2005-08-23
WinRar is a *Windows* program. Why would you be trying to run a Windows program in Linux without WINE?

---

### Post by WirelessMike on 2005-08-23
Depends upon what format you have the package in.  Is it a deb package?  rpm?  Perhaps it is tar.  I don't use winrar on linux (though it is an excellent program, imo), so I'm unfamiliar with that one.

Thing is--  You'll likely find what you're looking for at [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Stormy Eyes on 2005-08-23
[HOWTO for installing commandline rar tool in linux](http://ubuntuguide.org/#rar)

---

### Post by Kapre on 2005-08-23
[QUOTE=evansa4]Hi guys i want to know how to install download progams i know how to install progams in synaptic package manger but i dont know how to install progam i have download EG i have download winrar for linuxs but dontknow how to install it is there any steps u can tech me thanks[/QUOTE]
 evansa4 - if your intentions is to use the program to unpack/pack files, there is the RAR and UNRAR program in Synaptic which I think does the same as WinRar.

---

### Post by aysiu on 2005-08-23
[QUOTE=Kapre]evansa4 - if your intentions is to use the program to unpack/pack files, there is the RAR and UNRAR program in Synaptic which I think does the same as WinRar.[/QUOTE] Yes, it's called unrar. So, you can search for it on Synaptic, or you can just *sudo apt-get install unrar*. You don't need to download a separate file.

---

