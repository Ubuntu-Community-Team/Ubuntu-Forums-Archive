---
title: "Cant play DVD"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2006-07-18
I am new to Linux and so far I like it but I am having trouble with the Movie Player. I get these two error messages. Any way to fix this?

Totem could not play 'dvd:///media/cdrom0'.
No URI handler implemented for "dvd".

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this media.

---

### Post by Arisna on 2006-07-18
See this page:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by Fass on 2006-07-18
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bigken on 2006-07-18
install automatix and this will sort all your codec problems ;)

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by Sonic Alpha on 2006-07-18
You need to install all the restricted format packages.

Try [Automatix]("http://www.getautomatix.com"), it should download everything you need.

If not, try [this]("https://wiki.ubuntu.com/RestrictedFormats").

---

### Post by linuxuser28 on 2006-07-18
Went to Automatix but could not add this line to the source.list

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

Do I need to log in as root, and if so how do I do that.

---

### Post by Arisna on 2006-07-18
You need to have root privileges, which Ubuntu handles through sudo.  To edit that file as root, use the following:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by linuxuser28 on 2006-07-18
This is what I get when I enter that line in.

(gedit:11375): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Arisna on 2006-07-18
In that case, try `sudo nano -w /etc/apt/sources.list'.

This will use a terminal-based editor.  You will have to navigate with arrow keys and save the file using Ctrl-o.

---

### Post by bigken on 2006-07-19
sudo gedit /etc/apt/sources.list

---

### Post by linuxuser28 on 2006-08-10
I solved this problem by installing Easy Ubuntu and using Kaffenine instead of Movie Player. :D

---

### Post by bluemarble on 2006-09-07
> I am new to Linux and so far I like it but I am having trouble with the Movie Player. I get these two error messages. Any way to fix this?

Totem could not play 'dvd:///media/cdrom0'.
No URI handler implemented for "dvd".

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this media.

Hiya,

I have the same problem i have install all restricted formats, codecs, easyubuntu and automatix but DVDs still dont play.

I install automatix in brezzy, do i need to do it again for drapper?

I wanna watch DVD ;(

---

### Post by Frank Golden on 2006-09-07
> **linuxuser28 said:**
> This is what I get when I enter that line in.

(gedit:11375): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
I think that warnimg is false I read about a bug report related to this, don't remember where I saw it. You should still be able to
use the gedit editor. gksudo is recomended for GUI programs
like gedit.

---

### Post by bigken on 2006-09-08
cant see any harm in rerunning automatix ;)

---

### Post by CaveRat on 2006-09-08
I tried watching a rental DVD last night that refused to play on the computer, but worked fine in the home DVD player. Two other movies worked fine on the computer. Is there still some (not sure how to put this) crypts that are not compatible with Linux yet? Also is there any way to find out which codec is needed to play certain DVD's?

---

### Post by anaconda on 2006-09-08
To play encrypted DVD:s you need to install

libdvdcss

(or is it now libdvdcss2  ??)
howto install it is described in the "restrictdFormats" page someone gave a link in this thread already..

PS. not all DVD:s use css encryption. That is why some dvd:s work even without libdvdcss..

---

### Post by CaveRat on 2006-09-08
> **anaconda said:**
> To play encrypted DVD:s you need to install

libdvdcss

(or is it now libdvdcss2  ??)
howto install it is described in the "restrictdFormats" page someone gave a link in this thread already..

PS. not all DVD:s use css encryption. That is why some dvd:s work even without libdvdcss..

Thanks. Already did that after reading a similar thread a few days ago with that fix. I also have all the codecs installed. I could not play any DVD's beforehand. This one acted rather strange. I opened it with MPlayer and it gave me the tracks list. It refused to start the first track, started the second track, but stopped within say 10 seconds. I gave up after a few tries. I then slid it into my home DVD player and found out it's one of Sony's disks. Do they have an encryption that can't be hacked?

---

### Post by gn2 on 2006-09-08
Recent Sony discs are reasonably well protected, lately I have had to revert to Power DVD under Windows with "AnyDVD" installed and running to wiew some rental DVD's on my PC. Don't know if there's a Linux equivalent of AnyDVD, anybody?

---

