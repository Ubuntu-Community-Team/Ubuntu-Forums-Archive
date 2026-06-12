---
title: "Hard time installing custom versions of applications"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Ondkloss on 2007-10-22
I've got some 'specific demands' for my torrent applications, so I need specific versions.
I've tried Azureus 2.5.0.4 without any luck. Seems there is some Java error (still trying to figure it out).

Anyways, I went over to trying rtorrent, but I'm getting a old version from apt-get, so I want to do a manual install from a downloaded file. unfortunatly I'm not as into Ubuntu as I apparently should be. I've figured out the 'standard procedure' of doing "./configure", "make", "checkinstall", problem is the "./configure" part almost always gives me a missing library error. where am I suppose to find these/how do I correct that error? I read that in most of the cases the libraries exist but some sort of documentation was missing. Is this correct? Anyways, I need some help badly becouse at the moment I'm really stuck with using what apt-get offers. Tyty!

---

### Post by Pumalite on 2007-10-22
Use ktorrent. You can get it through Synaptic. I have used for a long time. No complaints. I also have Azureus, but I don't use it.

---

### Post by Maestro23 on 2007-10-22
When installing from source, 1st thing you need is "build-essential".

> sudo apt-get install build-essential

*As you keep running into dependency issues, you will have to keep satisfying them.  All can be found in the Ubuntu Repositories.  You can use the GuI (Synaptic) to search for and install these.

Hope that helps.  Good luck.:)

---

### Post by Maestro23 on 2007-10-22
> **Pumalite said:**
> Use ktorrent. You can get it through Synaptic. I have used for a long time. No complaints. I also have Azureus, but I don't use it.

I use Ktorrent as well.

---

### Post by stijngysemans on 2007-10-22
I also first tried Azureus, because I was used to this app under windows, but it doesn't same to work that well under Ubuntu.
I also use Ktorrent, this installs easy: just go to "applications >> add / remove ..." and search and install ktorrent. This even works good under gnome.

---

### Post by philinux on 2007-10-22
I've been using Deluge, it seems to fit the bill.

and there's an easy to install deb file for feisty and gutsy too. 

[http://deluge-torrent.org/downloads](http://deluge-torrent.org/downloads)

---

### Post by Ondkloss on 2007-10-22
Problem is I either have to use Azereus 2.5.0.4 or one of the newest stable releases of rTorrent (0.7.6 - 0.7.8), so any other advice than getting one of those to work isn't really helping me out alot :(

anyways, I already have build-essentials, and I've got rTorrent 0.7.7 lying around. so I start of with "./configure" and it generates this error:
```

checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for execinfo.h... yes
checking for proper overloaded template function disambiguation... yes
checking for library containing add_wch... no
checking for library containing wbkgdset... no
*** The ncurses library is required!

```

what am I suppose to search for in synaptic to find this one? I've had same type of error that said I was missing GTK+ library. seems it's a reccurring problem, and I'd like to know what specific packages I'm lacking that I'll have to find in Synaptic to get it working.

Thanks for all the replies!

---

### Post by Pumalite on 2007-10-22
Synaptic>Search>rtorrent>Install

---

### Post by adamorjames on 2007-10-22
sudo apt-get install libncurses5 and maybe libncurses5-dev and maybe libncurses-ruby and maybe... :lol:

---

### Post by Ondkloss on 2007-10-22
so basicly if a library is missing.... I just gotta install random packages with almost matching names until it works...?

-- so obv. since ktorrent was given such a good rep. here I searched and figured v2.2.2 was good enuff, problem is synaptic installs 2.2.1, so I got 2.2.2 from the net and tried "./configure". turns out it's missing "X libraries", seems missing libraries is a common thing when doing custom installs and I'm still unable to figure some good way of finding out what your really missing when you get a msg of that type...

---

### Post by adamorjames on 2007-10-22
> **Ondkloss said:**
> so basicly if a library is missing.... I just gotta install random packages with almost matching names until it works...?

Be glad libraries are packaged.

---

### Post by jaybombalous on 2007-10-22
> The ncurses library is required


did u have a brain fart or something, u need to do a search for ncurse in synaptic and see what shows up.

This is the description for libncursesw5 in synaptic

> Shared libraries for terminal handling (wide character support) 
This package contains the shared libraries necessary to run programs
compiled with ncursesw, which includes support for wide characters.

this is the description for libncursesw5-dev

> Developer's libraries for ncursesw 
This package contains the header files, static libraries
and symbolic links that developers using ncursesw will need.

This package includes support for wide characters.


when compiling source, u are the developer!!!! :) or so GCC thinks so...

---

### Post by Ondkloss on 2007-10-22
ye actually your right, the ncurses one was an easy one... but X library and GTK+ library there are very few packages for, and none of the ones I tried did any good.

and yes, I am still posting in the "Beginner Talk" forum for a reason -_-
still I'm finding custom version installations to be one of the hardest things to handle so far...

---

