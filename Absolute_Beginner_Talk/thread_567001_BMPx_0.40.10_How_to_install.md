---
title: "BMPx 0.40.10 How to install?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-04
I've just download the latest BMPx from their website: 0.40.10

And I really don't know how to run / install it...

Does someone have some precompiled deb? 

Thank you guys

---

### Post by Rui Pais on 2007-10-04
If you don't want to compile sources you've got this:
[http://www.getdeb.net/search.php?keywords=BMPx](http://www.getdeb.net/search.php?keywords=BMPx)
they have a 0.40.1

---

### Post by Kosimo on 2007-10-04
> **Rui Pais said:**
> If you don't want to compile sources you've got this:
[http://www.getdeb.net/search.php?keywords=BMPx](http://www.getdeb.net/search.php?keywords=BMPx)
they have a 0.40.1

That's exactly the version I have already ;)  But it really have some important bugs fixed on next releases. So, the point is to use the 0.40.10.

Thank you anyway.

---

### Post by Kosimo on 2007-10-04
OK, nobody have it :)

So, anyone knows at least how to build my own deb having the source?

Thanks again

---

### Post by Rui Pais on 2007-10-04
... ***** ok , what i posted here before was incorrect** *** ...

i managed to install the full list of dependencies (or it seems so), but i've found problem when compiling.
i'm trying now with a different set, if it goes ok i'll let you know...

---

### Post by Rui Pais on 2007-10-04
Ok,
here it goes a mini how-to. 
I installed under Feisty 64bits it should work equally with 32bits.
[B]
1. [/B]Install main typical tools:
```
sudo apt-get install build-essential checkinstall
```
**2.** Install dependencies:
```
sudo apt-get install boost-build libboost-dev libboost-regex-dev libboost-iostreams-dev libboost-thread-dev libsoup2.2-dev libglibmm-2.4-dev librsvg2-dev libgtkmm2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev libsexymm-dev libgstreamer0.10-dev libdbus-1-dev libdbus-glib-1-dev libstartup-notification0-dev libofa0-dev libcdparanoia0-dev 
```
**3.** Get bmpx code, decompress to a folder somewhere (it should create a folder named bmpx-0.40.10/) and go to the created folder with the code.
**4. **Configure compilation (no root powers needed):
```
./configure
```
[COLOR="Blue"]if it fails don't go further!! Post the last lines of output here.[/COLOR]

**5. **Compile (no root powers needed)
```
make
```
**6.** Make your self a debian package (it will be installed too):
```
sudo checkinstall
```
**7.** enjoy your new bmpx and musical in general (i'm typing this at the sound of the suite in E minor BWV 996, played at  Otto's Baroque Musick radio station, :))

[ATTACH]45289[/ATTACH] [ATTACH]45290[/ATTACH] [ATTACH]45291[/ATTACH]

---

### Post by Kosimo on 2007-10-06
> **Rui Pais said:**
> Ok,
here it goes a mini how-to. 
I installed under Feisty 64bits it should work equally with 32bits.
[B]
1. [/B]Install main typical tools:
```
sudo apt-get install build-essential checkinstall
```
**2.** Install dependencies:
```
sudo apt-get install boost-build libboost-dev libboost-regex-dev libboost-iostreams-dev libboost-thread-dev libsoup2.2-dev libglibmm-2.4-dev librsvg2-dev libgtkmm2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev libsexymm-dev libgstreamer0.10-dev libdbus-1-dev libdbus-glib-1-dev libstartup-notification0-dev libofa0-dev libcdparanoia0-dev 
```
**3.** Get bmpx code, decompress to a folder somewhere (it should create a folder named bmpx-0.40.10/) and go to the created folder with the code.
**4. **Configure compilation (no root powers needed):
```
./configure
```
[COLOR="Blue"]if it fails don't go further!! Post the last lines of output here.[/COLOR]

**5. **Compile (no root powers needed)
```
make
```
**6.** Make your self a debian package (it will be installed too):
```
sudo checkinstall
```
**7.** enjoy your new bmpx and musical in general (i'm typing this at the sound of the suite in E minor BWV 996, played at  Otto's Baroque Musick radio station, :))

[ATTACH]45289[/ATTACH] [ATTACH]45290[/ATTACH] [ATTACH]45291[/ATTACH]

Hi ya!

Thank yo soo much for your tutorial ;)
I'm trying to follow it but I'm having problems since the first step.... :( Ouch!

It looks like I have a very strange version of libc6-dev so. Here's the message I got:

> sudo apt-get install build-essential checkinstall
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages



Any idea?

Thank you again mate.

---

### Post by Rui Pais on 2007-10-08
Hi Kosimodo, sorry the late answer i was out of town.

You seems to have an incompatibility with libc6/libc6-dev. 
That is usually consequence of bad/mixed sources list, use of Automatix or random installation of debs from the net. It's nothing good. It's the first step to a broken system.

There are plenty of threads on that problem (that has nothing to do with BMPx, of course) maybe searching one and follow some instructions. 
You can post here your /etc/apt/sources.list and i'll give a look at it.

Btw, what are your Ubuntu version an platform?

---

