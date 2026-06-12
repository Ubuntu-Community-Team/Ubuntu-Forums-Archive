---
title: "alternative to DVD Shrink"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-06-04
Is there an linux alternative to DVD Shrink? or some other way to shrink a DVD_R?

---

### Post by bluevoodoo1 on 2006-06-04
I've used "dvdrip," and there's also "acidrip," which I haven't used.

---

### Post by dalonso on 2006-06-04
acidrip works well here, have not compared to any other tool however.

---

### Post by Nikusan on 2006-06-05
[QUOTE=mrvgarg]Is there an linux alternative to DVD Shrink? or some other way to shrink a DVD_R?[/QUOTE]

Try k9copy. DVD Shrink also works great with wine, so you could go that route if you want.

---

### Post by nalmeth on 2006-06-05
I've used DVD-Shrink in wine, and it work's good. Follow a howto to set that up, I think there's even one in the forums here. Google will hit it first page.

I've heard such great things about K9copy, you might want to try that..

Also I've heard there is xdvdshrink for linux, but haven't tried it either.

---

### Post by feight on 2006-06-05
The Acidrip program has a small problem that does not allow you to run the script within the gui, but it gives you a very good insight into how mencoder works and if you look at the output from the debug mode it gives you nearly the exact command you need to enter to take a DVD and rip it and put it through the encoding process in almost one step. 
DVD::RIP gave me problems out of the box both in AMD_64 and i386 versions in Dapper.

---

### Post by stackcheese on 2006-06-05
Do any of these programs have something familiar to DVDFab? Instead of having 1 dvd to 1 dvd-r are there any programs that can split the dvd to two single layer dvd's?

Thanks

---

### Post by dgkulzer on 2006-06-05
dvd shrink will work with Ubuntu. I havent tried it yet but here is a guide:
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

This guy has a pretty good site with lots of info.

---

### Post by richbarna on 2006-06-05
I had a problem getting dvdshrink to copy from dvd, so I use k9 copy to get the dvd onto the hard drive and then shrink it with dvd shrink from the folder, and that works fine.

---

### Post by jethro10 on 2006-06-05
[QUOTE=nalmeth]I've used DVD-Shrink in wine, and it work's good. Follow a howto to set that up, I think there's even one in the forums here. Google will hit it first page.

I've heard such great things about K9copy, you might want to try that..

Also I've heard there is xdvdshrink for linux, but haven't tried it either.[/QUOTE]

Every time I tried K9Copy it made iso's bigger than it said, too big to fit on a disk...
J

---

### Post by richbarna on 2006-06-05
[QUOTE=jethro10]Every time I tried K9Copy it made iso's bigger than it said, too big to fit on a disk...
J[/QUOTE]

K9Copy them to hard drive THEN dvd shrink them.

---

### Post by jamesrl on 2006-06-05
K9copy version 1.0.4 works great (e.g., will copy menus, shrink to fit on dvd correctly, etc.), however version 1.0.2 which is in the dapper repositories still had lots of bugs for me, but i got 1.0.4 working from source without too much hassle (getting dvd shrink fully working under wine seems more difficult and buggy).  
Basically you download the source from k9copy.sourceforge.net, untar/zip the file to a directory

> tar xvfz k9copy-1.0.4-2.tar.gz

> cd k9copy-1.0.4-2

> ./configure

At this point I got a few errors and had to install some extra packages via synaptic/apt-get: libdvdread3-dev, kdebase-dev, kdelibs4-dev, libqt3-mt-dev, qt3-dev-tools, libqt3-headers, libjpeg62-dev (and the associated dependencies).  This is probably not all the packages needed (e.g. already had libdvdread3, gcc installed), and I am not 100% certain all the packages are necessary to install as I just matched error messages in the install process to closest package in synaptic and then tried again and the messages went away. 

So install those packages and rerun configure and when it says everythings good at the end and says "start make now" then

> make

Hopefully everything runs smoothly after this step (actually this was the step where I found out I had to add libdvdread3-dev), then you just have to install it by

> sudo make install

And it should be installed.  To run type 

> /usr/local/kde/bin/k9copy

For convenience it may help to make a link to a directory in your path (im running gnome so the kde/bin isn't in my path) by say 

> sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy

Hope this helps people trying to get k9copy working to legally backup personal dvds.
cheers,


[Recently fixed error qt-dev-tools is actually qt3-dev-tools.]

---

### Post by manicka on 2006-06-05
[QUOTE=dgkulzer]dvd shrink will work with Ubuntu. I havent tried it yet but here is a guide:
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

This guy has a pretty good site with lots of info.[/QUOTE]


That guide is written for Hoary. It won't work with Breezy or Dapper.

This guide is written for Breezy, but should be pretty much the same for Dapper

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

---

### Post by ohgod on 2006-06-23
I got DVD Shrink & DVD Decrypter working fine under Dapper.  The guide manicka referenced should work.  Just make sure you tell wine to emulate NT 4.0 and change the drive type of your cdrom mount point to 'cdrom' (it'll be setup as a hard drive by default) and you should be good to go.

---

### Post by manicka on 2006-06-24
DVD Shrink now has a wiki page dedicated to it with the latest how-to

[https://wiki.ubuntu.com/DVDShrink](https://wiki.ubuntu.com/DVDShrink)

---

### Post by denisesballs on 2006-06-28
[QUOTE=jamesrl]For convenience it may help to make a link to a directory in your path (im running gnome so the kde/bin isn't in my path) by say 

> sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy[/QUOTE]

If you install with checkinstall instead of make install you don't need to do this. Or at least I didn't.

---

### Post by abowman on 2006-07-19
Here is a howto I put together explaining how I compiled k9copy on a clean installation of dapper:
[http://abowman.com/2006/07/18/scratch-copies-of-your-dvds/](http://abowman.com/2006/07/18/scratch-copies-of-your-dvds/)
k9copy is fast!  Takes about 15-20 minutes to copy a dvd.

---

### Post by crispy_420 on 2006-07-20
I have used k9copy with luck. 

And xDVDShrink works OK as well. For this one I downloaded the RPM version and used alien to convert to DEB file. It couldn't hurt to try it out.

---

### Post by berteh on 2007-05-23
> **jamesrl said:**
> had to install some extra packages via synaptic/apt-get: libdvdread3-dev, kdebase-dev, kdelibs4-dev, libqt3-mt-dev, qt3-dev-tools, libqt3-headers, libjpeg62-dev (and the associated dependencies).

I needed to add libhal-dev and libk3b-dev too.

thanks for this list of libraries, saved me some compiles ;)

---

### Post by Eddie Wilson on 2007-05-23
Will these packages copy the newest dvds that I've bought?
Eddie

---

### Post by berteh on 2007-05-23
> **Eddie Wilson said:**
> Will these packages copy the newest dvds that I've bought?
Eddie

I guess you'll be able to if you can play them using libdvdcss2; from [https://help.ubuntu.com/community/K9Copy:](https://help.ubuntu.com/community/K9Copy:)

You need to install libdvdcss2 to have support for encrypted DVD playback. To do this, enter the following, one line at a time, in the terminal:

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for more information on playing encrypted DVDs and other non-free media.

---

