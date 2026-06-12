---
title: "help with conflicting libraries/packages"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by neilw on 2006-07-20
Hello,
I have tried to install Grisbi money program, but it needed the libofx1 package, so I got that but the libofx1 package wanted libosp4 package.

It successfully installed libosp4, then on installing libofx1 I got this message:

Failed to install package 'libofx1_0.7.0-7_i386.deb'
dpkg: regarding /tmp/libofx1_0.7.0-7_i386.deb containing libofx1:
 ofx conflicts with libofx1
 libofx1 (version 1:0.7.0-7) is to be installed.
dpkg: error processing /tmp/libofx1_0.7.0-7_i386.deb (--install):
 conflicting packages - not installing libofx1

I really don't have a clue how to fix it as I'm a complete newbie to linux. Looking in the /usr/lib directory I can see a libofx.so.2 file (and a similar one in /usr/share), and that's about it.

My machine is a a basic unbuntu 6.06 install with Automatix and 'build-essentials' packages put on.

Any help would be much appreciated as I'd really like to use this software (as MS Money is the only package left I don't have a replacement for) and would also like to learn about how to fix these file conflicts :)

Neil.

---

### Post by catlett on 2006-07-20
[http://www.gnucash.org/](http://www.gnucash.org/) This is a link for gnu cash. It may be an alternative to grisbi money.
To install, enter these commands in the terminal. One at a time.
```
sudo apt-get install gnucash
```
```
 sudo rm -fr /usr/share/gnome/apps/Applications/ 
```
```
sudo gedit /usr/share/applications/GnuCash.desktop
```
After the last command a text editor will open, Enter this into the document. Make sure you copy it as it is. Do not put it all on one line. It has to look like this.
```
[Desktop Entry]
Name=GnuCash
Comment=GnuCash Personal Finance
Exec=gnucash
Icon=/usr/share/pixmaps/gnucash/gnucash-icon.png
Terminal=false
Type=Application
Categories=Application;Office;
```
Save the document. After that you will see gncash under Applications<Office<GnuCash
You may have to restart for the entry to apear.

As far as your dependency issues, try running an update with aptitude 
```
sudo aptitude update
```
```
sudo aptitude upgrade
```
Other than that, you may not be able to resolve the dependency issue.

---

### Post by neilw on 2006-07-20
Hello,
Thanks. I tried gnucash but didn't like it.

I think I found the problem, I removed the existing 'ofx' library and it worked, however I didn't realise grisli was in the synaptic package list and this was newer than the version at the grisli site. So, on installing the newer grisli it decided the verison I put on was wrong and it removed it and put on the one I removed ;)

So the moral I guess is to checked the advanced mode of synaptic to see if the package you want is there.

As for your reply, what do you mean it may not be fixable. I thought 'dll hell' was restricted to windows. What exactly is the problem, as surely any problem is fixable?

Thanks again.

Neil.

---

### Post by catlett on 2006-07-20
the prodlem is all linux distros aren't built upon the same libraries. You can have a linux application but it mat not work on your linux distro.
There is a movement to create a linux "standard" so applications can be built to that standard and will work on all distros. (Just in case you interested in further reading [http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base) )
The best way to acquire an application is to search synaptic package manager. If an application is in there it will work on your ubuntu box.
The next best it to look for a deb file. A deb is a debian package. Ubuntu is based on debian so most debs will work on ubuntu, but not all.
The least compatable but still possible is a tar file. a tar is a compressed file. It will usually hold binaries or an install script if you are lucky. These are the ones with the dependency issues because it hasn't been tailored to your distro.

---

### Post by neilw on 2006-07-20
Thanks, you've been very helpful. I've bookmarked the link and it reads as if Red Hat are trying to exert their power over others to use their standard rather than a common standard.

As for the package, I got the deb file, I just assumed because the libraries were different versions it would happily install them. However, not to worry it is up and running now and seems just what I wanted (well, I did want to try kmymoney but I'm happy with Gnome so will not bother).

---

### Post by catlett on 2006-07-20
Glad your up and running. Red Hat is the big guy in linux. Big in Europe, especially in Germany. But Debian systems are very popular now, Ubuntu being the new darling of the distro world.
debs usually will install but your debain based install my be above or below the libraries the package was written to. It can be a pain. That's why I'm hopeful the Standard really happens. If it does happen, then linux can have the equivalent of a windows exe. file. Then a linux app can easily be installed. 
That will be huge because that is a huge issue with mainstream people coming to linux. If people can find an application they want and point/click to activate an installer, then linux will be a viable alternative.
Good luck and remember search synaptic first and you can also search here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

