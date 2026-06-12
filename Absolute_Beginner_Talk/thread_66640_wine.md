---
title: "wine"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by airjrdn on 2005-09-17
I'd like to get [http://www.kyodai.com/](http://www.kyodai.com/) working under Ubuntu.  I just installed Breezy, but don't know much about how to do Wine.  I saw that I can install Wine from the system update, but do I also need to install DirectX?  Also, once I get that going, how do I run the windows .exe installation file?

---

### Post by jorgepeixoto on 2005-09-17
I am not a wine expert, but from what I know it is not a good idea to install directx under wine. And it may be a good idea to use the sidenet script which you can find in the following page : [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html) . After downloading and unpacking the sidenet tar file, read the readme and then run the script by entering the command ./setup in the directory where you unpacked it. This script will configure wine for you. You may try to install DCOM 98 or Windows Installer to help your program work (read the readme for more details).
 I do not know this program you speak about, but if it relies on directx it may be a good idea to try to run it under cedega (a program derived from wine with enhanced directx support).
And it is always a good idea to take a look at the site [http://frankscorner.org/](http://frankscorner.org/) , which was where I learned about sidenet in the first place.

---

