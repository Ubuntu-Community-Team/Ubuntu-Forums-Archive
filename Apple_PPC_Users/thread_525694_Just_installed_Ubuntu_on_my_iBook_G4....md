---
title: "Just installed Ubuntu on my iBook G4..."
date: 2007-08-14
forum: Apple PPC Users
---

### Post by makinasvp on 2007-08-14
But I am having trouble connecting to the internet wireless... Any thoughts?
Please help! Thank you :)

---

### Post by makinasvp on 2007-08-14
I have no idea what I am doing... I tried doing the sudo apt-get install bcm43xx-fwcutter, and now I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

in the terminal...
I tried sudo apt-get update, I get the same error in the terminal. 
Somebody please help!!

---

### Post by makinasvp on 2007-08-14
I don't know if this is relevant or not but I thought I would post these in case...

[IMG]http://i20.photobucket.com/albums/b248/SlowSRT/Screenshot.png[/IMG]

[IMG]http://i20.photobucket.com/albums/b248/SlowSRT/Screenshot-1.png[/IMG]

---

### Post by pxwpxw on 2007-08-14
Seems to be a problem with wl_apsta gone missing from [http://boredklink.googlepages.com](http://boredklink.googlepages.com)

Just tried it here too, similar result, no firmware installed. Need to run manual install with bcm43xx-fwcutter. [http://boredklink.googlepages.com/ubuntuguide](http://boredklink.googlepages.com/ubuntuguide), or see the manual.

There are alternative sources for wl_apsta, including MacosX i think. I need this also (and for an iBookg4). I will post when/if I find the answer.

Heres what I got with a retry --

[http://boredklink.googlepages.com/ubuntuguide](http://boredklink.googlepages.com/ubuntuguide)

madmax@ibook:~$ sudo dpkg --configure bcm43xx-fwcutter
Setting up bcm43xx-fwcutter (006-1) ...
--12:42:46--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:42:47 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
madmax@ibook:~$

---

### Post by emphyrio on 2007-08-14
I am getting the same error re: the broken link when I am trying to install  bcm43xx-fwcutter too.  If/when I find a solution, I'll post it here, if one hasn't already been posted.

---

### Post by pxwpxw on 2007-08-15
[http://ubuntuforums.org/showpost.php?p=3151284&postcount=906](http://ubuntuforums.org/showpost.php?p=3151284&postcount=906)

and see the other posts, but still looking for a usable wp_apsta.o,  alternative is extract from macosx if you have it. More when I have it.

---

### Post by stmiller on 2007-08-15
You can extract the firmware from a Mac OS X driver download. There are some threads on this on the ppc section of [http://forums.gentoo.org](http://forums.gentoo.org) .

---

### Post by makinasvp on 2007-08-15
> **pxwpxw said:**
> Seems to be a problem with wl_apsta gone missing from [http://boredklink.googlepages.com](http://boredklink.googlepages.com)

Just tried it here too, similar result, no firmware installed. Need to run manual install with bcm43xx-fwcutter. [http://boredklink.googlepages.com/ubuntuguide](http://boredklink.googlepages.com/ubuntuguide), or see the manual.

There are alternative sources for wl_apsta, including MacosX i think. I need this also (and for an iBookg4). I will post when/if I find the answer.

Heres what I got with a retry --

[http://boredklink.googlepages.com/ubuntuguide](http://boredklink.googlepages.com/ubuntuguide)

madmax@ibook:~$ sudo dpkg --configure bcm43xx-fwcutter
Setting up bcm43xx-fwcutter (006-1) ...
--12:42:46--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:42:47 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
madmax@ibook:~$

Oh my goodness!! I get the exact same error lol

---

### Post by pxwpxw on 2007-08-15
I found this easiest, works on iBookG4, also G5 (but some bugs in iwlist for G5)
Uses GTK installer with its own set of firmware files.
Just follow steps 1-6.

 HOWTO: Broadcom 43xx based wireless cards the EASY way.
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

This will download the installer (link is in howto also)
[http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.1.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.1.tar.gz)

==============
Other sources for manual extraction using bcm43xx-fwcutter -w /lib/firmware <file>

[http://ubuntuforums.org/showpost.php?p=3151213&postcount=905](http://ubuntuforums.org/showpost.php?p=3151213&postcount=905)
[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)

If you dont have internet but do have macosx:

MacosX /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2.
============

---

### Post by makinasvp on 2007-08-15
> **pxwpxw said:**
> I found this easiest, works on iBookG4, also G5 (but some bugs in iwlist for G5)
Uses GTK installer with its own set of firmware files.
Just follow steps 1-6.

 HOWTO: Broadcom 43xx based wireless cards the EASY way.
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

This will download the installer (link is in howto also)
[http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.1.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.1.tar.gz)

==============
Other sources for manual extraction using bcm43xx-fwcutter -w /lib/firmware <file>

[http://ubuntuforums.org/showpost.php?p=3151213&postcount=905](http://ubuntuforums.org/showpost.php?p=3151213&postcount=905)
[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)

If you dont have internet but do have macosx:

MacosX /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2.
============

SUPER!!! It WORKED!! WOOHOO! You are awesome, thank you so much!

---

