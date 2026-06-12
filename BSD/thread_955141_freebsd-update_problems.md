---
title: "freebsd-update problems"
date: 2008-10-21
forum: BSD
---

### Post by kk0sse54 on 2008-10-21
So I've come back to FreeBSD again after a while and I have to say it's a great system but some of the problems I've been getting make me wonder whether I should just go back to NetBSD despite it's own various shortcomings (flash, Xfree86 by default, mp3 playback). The problems I've been having with FreeBSD have to do with trying to update my system either through freebsd-update, portmanager, or to update the ports portsnap. I've already thrown portmanager out the window because it takes literally days to compile and upgrade one package(Opera in this case) :mad:.

The problem I'm getting with freebsd-update is that I'll try ```
freebsd-update fetch
```
and it returns "Looking up update.FreeBSD.org mirrors... 1 mirrors found.
Fetching metadata signature for 7.1-PRERELEASE from update1.FreeBSD.org... failed.
No mirrors remaining, giving up." It won't let me upgrade to a later release number either. The closest thing I found on google was some key errors but no solutions and the folks in #freebsd weren't too helpful either (Probably because I entered in on one of their linsux rants :roll:). If any body has a solution I would be greatly appreciative :)

---

### Post by cardinals_fan on 2008-10-21
> **C!oud said:**
> So I've come back to FreeBSD again after a while and I have to say it's a great system but some of the problems I've been getting make me wonder whether I should just go back to NetBSD despite it's own various shortcomings (flash, Xfree86 by default, mp3 playback). The problems I've been having with FreeBSD have to do with trying to update my system either through freebsd-update, portmanager, or to update the ports portsnap. I've already thrown portmanager out the window because it takes literally days to compile and upgrade one package(Opera in this case) :mad:.

I'm not enough of a FreeBSD guru to answer this, but I do have some experience using FreeBSD vs. NetBSD.  Flash is a fiasco in NetBSD, and 3D acceleration is nonexistant, but the default Xfree86 actually runs quite well on my card (I can't speak for yours), and you can definitely play mp3s.

I use NetBSD as my primary OS on my secondary machine, which could barely handle 3D stuff anyway.

---

### Post by angryfirelord on 2008-10-22
You're running a prerelease of 7.1, which means that it's not ready for production use. Therefore, the FreeBSD team doesn't issue binary security updates for 7.1 yet. (I take it that you are running PC-BSD?) If you install the 7.0 kernel, freebsd-update should work for you.

To answer the rest of your questions:

-If you want really decent 3D acceleration, nvidia is your only choice. Version 173.14.12 fixed a lot of issues I had with previous nvidia drivers, although I still run into some issues with applications. I'm sure that some of the open source drivers that have 3D (like ati & radeon) will work fine. 
-I don't know about flash 9, but you can install flash 7 by doing:
```
portinstall www/linux-flashplugin7 www/nspluginwrapper
nspluginwrapper -v -a -i
```
(execute nspluginwrapper as root & non-root)

If you get a command not found, then install portupgrade in ports-mgmt.

-I actually found this out a little while ago, but you can tell portinstall/portupgrade to use binary packages. By default, FreeBSD uses the packages-7.0-release section, but these packages are never upgraded. Instead, you can use packages-7-stable, which is fairly updated.
To do so, go to your home folder and open up your .cshrc file:
```
ee .cshrc
```
Add the following:
```
setenv PACKAGESITE ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-7-stable/Latest/
```
Substitute ftp.freebsd.org with a mirror of your choosing. (I used the Firefox extension Flagfox and tested each mirror in order to find one somewhat close to me)
[http://www.freebsd.org/doc/en/books/handbook/mirrors-ftp.html#HANDBOOK-MIRRORS-CHAPTER-SGML-MIRRORS-US-FTP]("http://www.freebsd.org/doc/en/books/handbook/mirrors-ftp.html#HANDBOOK-MIRRORS-CHAPTER-SGML-MIRRORS-US-FTP")

So for me, I set mine to:
```
setenv PACKAGESITE ftp://ftp7.us.freebsd.org/pub/FreeBSD/ports/i386/packages-7-stable/Latest/
```
Now, when you use portinstall, you can specify -P to use binary packages first, then source packages later, or -PP to only use binary packages. Be aware that some of the binary packages aren't QA checked. I found firefox3 to be a little...funky. I ended up compiling it and it worked fine.

-mp3 playback: [http://www.freebsd.org/doc/en/books/handbook/sound-mp3.html]("http://www.freebsd.org/doc/en/books/handbook/sound-mp3.html")

Basically, just do what you would normally do in Ubuntu and install the necessary codecs.

---

### Post by kk0sse54 on 2008-10-22
> **cardinals_fan said:**
> I'm not enough of a FreeBSD guru to answer this, but I do have some experience using FreeBSD vs. NetBSD.  Flash is a fiasco in NetBSD, and 3D acceleration is nonexistant, but the default Xfree86 actually runs quite well on my card (I can't speak for yours), and you can definitely play mp3s.

I use NetBSD as my primary OS on my secondary machine, which could barely handle 3D stuff anyway.

I really dislike Xfree86 so I'm considering doing a non graphical install and then later on install xorg, as for mp3 for some reason last time I used it I was having a lot of trouble getting it to work (well just my sound card in general). I don't care for 3D acceleration but flash is certianly a fiasco and I kinda need it for various things (although having to run linux version of flash in freebsd hasn't been much better either)


> **angryfirelord said:**
> You're running a prerelease of 7.1, which means that it's not ready for production use. Therefore, the FreeBSD team doesn't issue binary security updates for 7.1 yet. (I take it that you are running PC-BSD?) If you install the 7.0 kernel, freebsd-update should work for you.

To answer the rest of your questions:

-If you want really decent 3D acceleration, nvidia is your only choice. Version 173.14.12 fixed a lot of issues I had with previous nvidia drivers, although I still run into some issues with applications. I'm sure that some of the open source drivers that have 3D (like ati & radeon) will work fine. 
-I don't know about flash 9, but you can install flash 7 by doing:
```
portinstall www/linux-flashplugin7 www/nspluginwrapper
nspluginwrapper -v -a -i
```
(execute nspluginwrapper as root & non-root)

If you get a command not found, then install portupgrade in ports-mgmt.

-I actually found this out a little while ago, but you can tell portinstall/portupgrade to use binary packages. By default, FreeBSD uses the packages-7.0-release section, but these packages are never upgraded. Instead, you can use packages-7-stable, which is fairly updated.
To do so, go to your home folder and open up your .cshrc file:
```
ee .cshrc
```
Add the following:
```
setenv PACKAGESITE ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-7-stable/Latest/
```
Substitute ftp.freebsd.org with a mirror of your choosing. (I used the Firefox extension Flagfox and tested each mirror in order to find one somewhat close to me)
[http://www.freebsd.org/doc/en/books/handbook/mirrors-ftp.html#HANDBOOK-MIRRORS-CHAPTER-SGML-MIRRORS-US-FTP]("http://www.freebsd.org/doc/en/books/handbook/mirrors-ftp.html#HANDBOOK-MIRRORS-CHAPTER-SGML-MIRRORS-US-FTP")

So for me, I set mine to:
```
setenv PACKAGESITE ftp://ftp7.us.freebsd.org/pub/FreeBSD/ports/i386/packages-7-stable/Latest/
```
Now, when you use portinstall, you can specify -P to use binary packages first, then source packages later, or -PP to only use binary packages. Be aware that some of the binary packages aren't QA checked. I found firefox3 to be a little...funky. I ended up compiling it and it worked fine.

-mp3 playback: [http://www.freebsd.org/doc/en/books/handbook/sound-mp3.html]("http://www.freebsd.org/doc/en/books/handbook/sound-mp3.html")

Basically, just do what you would normally do in Ubuntu and install the necessary codecs.

I'm am  running the pre release of 7.1 FreeBSD not PC-BSD but updates are in fact being provided for 7.1-BETA and 7.1-BETA2 which I was trying to upgrade to but it can't find the metadata package so it fails and stops as a result. I have an ATI x600 video card which has been working with almost every linux distro I've tried but the open source radeon driver just doesn't perform as well as the proprietary one which isn't avialable for *BSD although it does provide 3D support which isn't that big of an issue for me. Thanks for the help with portupgrade but I already have it installed and mp3's work fine with FreeBSD it was NetBSD I was having trouble with.

Right now I don't see any benefit of running FreeBSD over NetBSD since most of the problems I've expierenced in NetBSD are present in FreeBSD as well so I think I'm just going to return to NetBSD. 
~thanks, C!oud

---

