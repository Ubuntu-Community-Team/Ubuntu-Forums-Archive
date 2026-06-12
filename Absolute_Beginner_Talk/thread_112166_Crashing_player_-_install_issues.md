---
title: "Crashing player - install issues?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by TikkiRo on 2006-01-03
[COLOR="Purple"]I installed an older version of Real Player as it seemed to be the easiest one to actually get on V8 as in rp8_linux20_libc6_i386_cs2_rpm.  Synpatic appeared to install it without any errors but every time I run it it totally crashes the system - have to reboot to release it.  I've tried reinstalling etc but getting nowhere.  I know I could push up to the V10, but had even bigger problems trying to figure out how to install that one, and this seemed simpler (to be able to let Synaptic do it).  Any suggestions on how to perhaps try and solve the problem?  If you really feel I need to upgrade to the 10 would anyone be up to a 'walk-through' after download of the file.  I have a reasonable understanding of the Terminal but still very lost in many parts.  Thanks :) [/COLOR]

---

### Post by dixonstalbert on 2006-01-03
hello tikkiro


Have you seen this guide?

[http://ubuntuguide.org/](http://ubuntuguide.org/)


I used it to install RealPlayer10 without a problem.

good luck

---

### Post by TikkiRo on 2006-01-04
[COLOR="Purple"]Hmm - yeh that was actually what seemed to cause most of my problems.  I kept getting error msgs after adding in the additional repositories in it mentioned in the sources list.  Then once I got the package downloaded it was in Bin or RPM format and I couldn't figure out how to install those since most others seemed to be simpler tarball types.  Perhaps I should have just read and not acted on the info :).  Will have another go, as it's really frustrating to not be able to listen to online streams.[/COLOR]

Ok - one step worse this time round - now get this error msg on doing the sudo apt-get install etc:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm the only user of the PC so now more stuck than ever. :(
TKR

---

### Post by dixonstalbert on 2006-01-04
hi again

I just noticed the guide has not upgraded to Breezy and refers still to the Hoary Ubuntu repositories- maybe that is what is giving you grief?

you can look in official Wiki for ubuntu (link at top of page) for instructions for adding extra repositories to Breezy edition of ubuntu. Or, seach forum for Automatix. 

Automatix is an excellent script that will add proper repositories then give you a menu for adding all sorts of good programs. After you run it if type sudo apt-get install realplay and you should be okay.

hope this helps

---

### Post by TikkiRo on 2006-01-05
Hmm-actually until you mentioned it I didn't realise I was actually using the older 5.04 version anyhow which Automatix doesn't seem to like running in or else I'm not using it right.  Anyway - downloading the newer UB version now so will start over and see if i can get some better results this time round.  Tks for the excellent pointer tho. :))

---

### Post by TikkiRo on 2006-01-06
Sorted - thanks to all who helped point me in the right direction for solutions here :)

---

