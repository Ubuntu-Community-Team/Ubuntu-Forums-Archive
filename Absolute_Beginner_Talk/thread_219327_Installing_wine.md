---
title: "Installing wine"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by LCC on 2006-07-19
I am triyng to install wine so I can run a few wndows programs in ubuntu 6.06
x_64 version, and I found at the wine site the code lines to install it in a 64-bit ubuntu but for some reason this happen...
------------------------------------------------------------------


Building Wine on Ubuntu / Kubuntu 6.06 (Dapper Drake)

First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries.

configure will find several omissions, but a few will only be noticed by the 'make' steps.

The following add links, that the library install does not make:

# Do this as *root* by hand, it won't work as a script as written.
cd /usr/lib32
ln -s libX11.so.6 libX11.so
ln -s libXext.so.6 libXext.so
ln -s libfreetype.so.6 libfreetype.so
[COLOR="Red"]ok till now I was doing fine[/COLOR]
Run configure, build and install with:

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"  ./configure
[COLOR="Red"]then after typing the above line this message comes up
-bash: ./configure: No such file or directory
[/COLOR]make depend
make all
sudo make install

Thanks for any help

---

### Post by ash211 on 2006-07-19
./configure is a command that runs configure in the directory you're in.  If you followed the instructions exactly as they're typed here, then you would still be in the /usr/lib32 folder (that's what cd does, change directories).  You need to cd into the directory where you downloaded the wine source code before beginning with that LDFLAGS line.

---

### Post by ash211 on 2006-07-19
If you haven't downloaded the wine source code yet, go to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and follow the "Getting source packages from the repository" header.  Then follow this code to download the source into a new folder:
```
mkdir ~/winesrc
cd ~/winesrc
sudo apt-get source wine
```
Then you should be able to continue with ```
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
make depend
make all
sudo make install
```
(I assume you're talking about this page: [http://www.winehq.com/?issue=317#Wine%20on%2064-bit%20AMD%20/%20Ubuntu](http://www.winehq.com/?issue=317#Wine%20on%2064-bit%20AMD%20/%20Ubuntu))

Alternatively, Kilz has a [how-to on this exact subject]("http://www.ubuntuforums.org/showthread.php?t=185557").

---

