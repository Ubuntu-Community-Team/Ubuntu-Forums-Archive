---
title: "Installing from a tarball"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by grte on 2005-12-11
Can anyone walk me through how you would install from a tarball?  Much as I love apt-get and synaptic, they just don't have everything I want, and I just don't know the correct commands for doing this.

---

### Post by Mordred on 2005-12-11
Before you try to install from tarball,
have you added extra repositories?

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

the program you are looking for may be there and 
you can install it with synaptic

---

### Post by grte on 2005-12-11
I have added the extra repositories, and I'm afraid the program I want isn't in them.

---

### Post by Gustav on 2005-12-11
the commands are:
```
tar xvfz <filename>
cd <filename> (or similar, the new directory anyway)
./configure
make
sudo make install
```
This works for most apps but if not check the README file.

---

### Post by grte on 2005-12-11
Thanks

---

### Post by freedom on 2005-12-11
Are you sure that out there in some repository not exist .deb package for that program you need? :)

Anyway...
My advice is to install "checkinstall" so when you install from tarball do
./configure (with some parameter if needed)
make
and instead of "make install" do
sudo checkinstall -D make install
That way you'll get your program installed and get a .deb package for your system. If someday you want to uninstall it just do
sudo dpkg -r <packagename>

---

### Post by BatsotO on 2005-12-11
Tarball dont include dependencies like apt do. When you do ./configure it will scan your system for all supporting files it may need. Sometime you'll have to install all the dependencies it misses manually before you can do make and make install.

---

### Post by artnay on 2005-12-11
[QUOTE=Gustav]the commands are:
```
tar xvfz <filename>
cd <filename> (or similar, the new directory anyway)
./configure
make
sudo make install
```
This works for most apps but if not check the README file.[/QUOTE]

Configure with --help is also useful. You most probably have to set prefix. I would not suggest using sudo make install, instead utilize the power of apt/dpkg. If it's not in repos, then compile it by yourself. Do "sudo apt-get install checkinstall" and replace "sudo make install" with "sudo checkinstall". That way you get Debian file (.deb) which can be removed easily if something went wrong (sudo dpkg -r package).

---

### Post by Gustav on 2005-12-11
[QUOTE=freedom]Are you sure that out there in some repository not exist .deb package for that program you need? :)

Anyway...
My advice is to install "checkinstall" so when you install from tarball do
./configure (with some parameter if needed)
make
and instead of "make install" do
sudo checkinstall -D make install
That way you'll get your program installed and get a .deb package for your system. If someday you want to uninstall it just do
sudo dpkg -r <packagename>[/QUOTE]
Thank you!
Thats much better.
(But you don't have to sudo dpkg -r <packagename>, checkinstall does that for you and you can UNINSTALL FROM SYNAPTIC OR APT and you don't need to keep the .deb file!!!)

---

### Post by grte on 2005-12-11
Thanks for all the advice, everybody.

---

