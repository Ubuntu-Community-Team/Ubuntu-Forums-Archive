---
title: "Compiling K9copy"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-25
I want to try out the newest version of K9copy from their website, so I downloaded the source, removed the old version that I had previously installed from the Ubuntu Repositories and such, and I am getting this error when compiling:

```
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
```

If anyone could give me some pointers on what I should do to fix the error, I would be greatly obliged.

By the way, here is their website:
[http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

And I downloaded Version 1.2.2 from source.
The reason I want to try out the newest version, is because when I am coping in a DVD, it is getting most of it, except for about 15 minutes of the ending. The DVD actually does have this 15 minute ending on it, as I can watch it when I play it was VLC, but it k9copy isn't getting it, so I wanted to try the newer version.

Thanks for any help :)
Dr Small

---

### Post by danillo on 2008-01-25
I'm not 100% sure, but it could be the xlibs-dev package that's missing.

---

### Post by gvartser on 2008-01-25
```
apt-cache search libx11
```
   libx11-6 - X11 client-side library
   libx11-6-dbg - X11 client-side library (debug package)
   libx11-data - X11 client-side library
   libx11-dev - X11 client-side library (development headers)
   libx11-freedesktop-desktopentry-perl - perl interface to Freedesktop.org .desktop files
   libx11-protocol-perl - Perl module for the X Window System Protocol, version 11

```
sudo apt-get install libx11-dev
```

That should do the trick

Best regz,
G

---

### Post by gvartser on 2008-01-25
Also read on K9Copy homepage that the following stuff also are required:
-> [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

    *  DVDAuthor
    * libdvdread
    * growisofs
    * mencoder
    * mplayer
    * libhal
    * libdbus
    * libdbus-qt

/g

---

### Post by Dr Small on 2008-01-25
> **danillo said:**
> I'm not 100% sure, but it could be the xlibs-dev package that's missing.
That worked. Now I'm getting:
```
checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (headers and libraries) not found. Please check your installation!
```

---

### Post by Dr Small on 2008-01-25
> **gvartser said:**
> Also read on K9Copy homepage that the following stuff also are required:
-> [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

    *  DVDAuthor
    * libdvdread
    * growisofs
    * mencoder
    * mplayer
    * libhal
    * libdbus
    * libdbus-qt

/g
Thanks, that is helpful.
I fixed the qt error, and now I'm getting a KDE error.

I previously had k9copy installed, and never removed any of the KDE libraries, so I thought that would pass. I guess I was wrong.
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

---

### Post by gvartser on 2008-01-25
qt4-dev-tools

or 

libdbus-qt

/g

---

### Post by gvartser on 2008-01-25
> **Dr Small said:**
> Thanks, that is helpful.
I fixed the qt error, and now I'm getting a KDE error.

I previously had k9copy installed, and never removed any of the KDE libraries, so I thought that would pass. I guess I was wrong.
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

I guess that you are running GNOME and not KDE.

Install the kde dev libs:

* kdebase-dev - development files for the KDE base module
* kdelibs4-dev - development files for the KDE core libraries

/g

---

### Post by gvartser on 2008-01-25
Hmm there is an Ubuntu ready package for k9copy, why not install that one, that way you do not have to handpick every missing development lib.

```
sudo apt-get install k9copy
``` 


/g

---

### Post by Incense on 2008-01-25
If you want to save yourself the headache, getdeb has the 1.2.2 deb, unless you're going for 1.9.7. I think you'll need KDE4 installed for that one. 

[http://www.getdeb.net/app/K9Copy]("http://www.getdeb.net/app/K9Copy") <-- for 1.2.2

---

### Post by nikoPSK on 2008-01-25
> **Incense said:**
> If you want to save yourself the headache, getdeb has the 1.2.2 deb, unless you're going for 1.9.7. I think you'll need KDE4 installed for that one. 

[http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy) <-- for 1.2.2

well, compiling for me didn't work, but the deb does, although it's older. :|

---

### Post by gvartser on 2008-01-25
I installed using apt-get and got v 1.1.3, guess that the deb package is better then with it's higher version.

/g

---

### Post by mc4man on 2008-01-25
if you did want to compile this or future versions a couple of complete step by's
[http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy)
would suggest using  ```
./configure --prefix=/usr
``` will make installing future versions easier
 dr. small - the missing 15 min. is interesting, would be surprised if latest version fixed, but you never know

---

### Post by Dr Small on 2008-01-27
I ended up installing the deb from getdeb.net, which wasn't exactly the newest version, but was close and it did the same thing. So after waisting so much time, I ran k9copy through the terminal, and it appears that there is a bad sector on the end of the disc.

The newer version crashed everytime it got to the end, because of the bad sector, whereas the older version just kept pluggin on even though it couldn't read the sector. So, the problem was my DVD the entire time.

Dr Small

---

### Post by nikoPSK on 2008-01-27
> **Dr Small said:**
> I ended up installing the deb from getdeb.net, which wasn't exactly the newest version, but was close and it did the same thing. So after waisting so much time, I ran k9copy through the terminal, and it appears that there is a bad sector on the end of the disc.

The newer version crashed everytime it got to the end, because of the bad sector, whereas the older version just kept pluggin on even though it couldn't read the sector. So, the problem was my DVD the entire time.

Dr Small

good that's all cleared up. :)

---

### Post by Dr Small on 2008-01-27
Yeah, but I never got the compiling down...

---

### Post by gvartser on 2008-01-28
Hmm maby dvdshrink in wine could had worked.

I used it a couple of times to shrink dvd's and it worked nicely.

/g

---

### Post by kpkeerthi on 2008-01-28
To install the dependencies needed for **compiling **k9copy, run
```
apt-get build-dep k9copy
```

[Here]("http://ubuntuforums.org/showthread.php?t=425802") is an old guide to compile k9copy from source but it should work if you install the dependencies as noted above

---

### Post by mc4man on 2008-01-30
I think the apt-get..... gives you almost everything - it seems you also need libavcodec-dev and maybe libavformat-dev

---

