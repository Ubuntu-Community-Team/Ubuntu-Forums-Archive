---
title: "Packaging help."
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by conor on 2006-05-29
I need help trying to create debian packages from outside source.  I read a tutorial on using checkinstall and I used it with a source snapshot of [Transmission]("http://transmission.m0k.org/").  It gave me [this .deb]("http://d.turboupload.com/d/641962/transmission_0.6-svn-r257-2006-05-25-1_i386.deb.html"):
```
./
usr/
usr/local/
usr/local/bin/
usr/local/bin/transmission-gtk
usr/local/bin/transmissioncli
usr/local/share/
usr/local/share/locale/
usr/local/share/locale/it/
usr/local/share/locale/it/LC_MESSAGES/
usr/local/share/locale/it/LC_MESSAGES/transmission-gtk.mo
usr/share/
usr/share/doc/
usr/share/doc/Transmission/
usr/share/doc/Transmission/AUTHORS
usr/share/doc/Transmission/LICENSE
usr/share/doc/Transmission/NEWS
usr/share/doc/Transmission/README
```
I want to get rid of the /usr/local/-----
and replace it with just /usr/------- like most ubuntu packages.  I also want to add an icon file to the package at /usr/share/pixmaps and attempt to create a menu item for it.  Is there anyway I can go about this?  

If you want to play around with it, the source I used can be found [here]("http://www.chucker.rasdi.net/opensource/transmission/Transmission-0.6-svn-r257-2006-05-25-Source.tar.bz2").  
I do want to learn though so please do not just do it for me.  ;)  THANKS!

---

### Post by ComplexNumber on 2006-05-29
or you could use alien instead of checkinstall. 

at the moment, i haven't got checkinstall installed, but to find out what options are availble that will allow you to specify the initial path (ie /usr), type in "checkinstall --help". i think it would probably be something like checkinstall -X --prefix=/usr (where X is the switch)

---

### Post by conor on 2006-05-30
Good news!  I fixed some of this, that is got the files in order but I didn't manage to add an icon or menu file.

[http://d.turboupload.com/d/647702/transmission_0.6-svn-r259-3_i386.deb.html](http://d.turboupload.com/d/647702/transmission_0.6-svn-r259-3_i386.deb.html)

Here are the files again though:

```
./
usr/
usr/bin/
usr/bin/transmission-gtk
usr/bin/transmissioncli
usr/man/
usr/man/man1/
usr/man/man1/transmissioncli.1.gz
usr/share/
usr/share/doc/
usr/share/doc/Transmission/
usr/share/doc/Transmission/AUTHORS
usr/share/doc/Transmission/LICENSE
usr/share/doc/Transmission/NEWS
usr/share/doc/Transmission/README
usr/share/locale/
usr/share/locale/it/
usr/share/locale/it/LC_MESSAGES/
usr/share/locale/it/LC_MESSAGES/transmission-gtk.mo
```

So just adding files to the source, how do I do this?

---

### Post by catlett on 2006-05-30
Just for your future reference. You can use alien to turn an rpm into a deb and then install it like any other deb. It makes life easy. That is how I installed transmission as a mater of fact. When I did the alien conversion to a deb I also got an icon. 
Just thougth I'd mention alien in case you didn't know of it.

---

### Post by conor on 2006-05-30
I knew thanks.  I was just using Transmission as a kind of Source experiment.  Thank you for the advice though.  I really appreciate it.

---

### Post by catlett on 2006-05-30
Sorry about that. I never found about things like that and I wished someone had told me. but your way ahead of me. Again sorry to bother you, no offense intended.
P.S. I downloaded your deb. I never used a site like that. Do you have to have an account or is it an imageshack kind of thing? (I also got a popup attack when I hit the download link:D )

---

### Post by conor on 2006-05-31
No need to apologise.  I did really apprecite that advice.   But Turboupload.com is free.  Its kind of slow to upload but it is getting better and better.  Yeah, unfortunately the popups are there, but they keep it free, use Adblock for Firefox to get rid of the popups.  :)

---

