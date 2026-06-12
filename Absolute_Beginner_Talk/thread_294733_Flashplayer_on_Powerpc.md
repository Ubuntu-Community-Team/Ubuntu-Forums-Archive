---
title: "Flashplayer on Powerpc?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Mushed Mango on 2006-11-07
I have a Powerpc, and I was trying to get the Flashplayer plugin for my web browsers. It says everywhere I try and look that the architecture is unsupported. Is there another version I could try?

---

### Post by 3rdalbum on 2006-11-07
There is an open-source project called Gnash, which will run on PowerPC. Unfortunately, to my knowledge, it's only distributed as source code (which means a trip to the command-line and a couple of apt-gets to compile it).

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

Unfortunately Adobe doesn't make a Flash Player for PPC Linux.

---

### Post by maddog39 on 2006-12-17
Okay, this is what I did on my PowerBook.

Firstly download and unpack the source package for gnash from the link provided above. Once that's done, install the dependencies required. I have alot of previously installed dev packages from other source packages that I compiled, so please update me on more configure errors anyone gets and i'll update these commands.

So, run this command in your terminal:
```

sudo apt-get install g++ libgtk2.0-dev libgtkglext1-dev libboost-dev libsdl1.2-dev libxml2-dev

```[EDIT]
I have found most of its primary dependencies required to compile on ubuntu atleast so now this command should work regardless, report if otherwise.
[EDIT 2]
Fixed the SDL version number, its 1.2 not 2.0. :) Also added another missing dependency, libxml2-dev.

Remeber, these are just the dependencies I needed. It's probably different for you and I don't have the complete list of them. So if it doesnt work, please post your errors and i will update this post with fixes.

Now, you want to change directory to where you unpacked the source package. Normally if you did this in firefox you probably downloaded it to your desktop. So in that case you would run the following command:
```

cd ~/Desktop/gnash-0.7.2

```Now, we want to actually compile it and so forth. So the first step to doing that is running the configure script. To do that simply run:
```

./configure

```Now, we're at the point where we need to build and install the application. If you made it this far and the configure script didnt give you some obscure error then your on the final stretch and shouldn't have anymore problems. To build (compile) and install the package simply enter the following command:
```

make && sudo make install

```When prompted for your password, simply enter your account password and it will proceed in installing the package. When it's finished, your done!

---

### Post by maddog39 on 2007-01-17
Okay, I have just created a debian package for gnash now. It doesnt check for dependencies so (forgot to add that) so you will need to install them if you dont have them. You can install them by running:
```
sudo apt-get install libgtkglext1 libboost libsdl1.2 libxml2
```
Then simply download the deb, double click on it, and let GDebi to the rest. :) You can download the debian package below:
[http://www.dx-h.com/downloads/gnash_0.7.2-1_powerpc.deb](http://www.dx-h.com/downloads/gnash_0.7.2-1_powerpc.deb)

Hope this helps! :D

---

