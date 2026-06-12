---
title: "what's the best browser?"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-05-10
Just out of interest, to khow what the rest of you think...

For speed on a relatively low spec machine PII 500 ish with 256 ram

my findings are:
Mozilla reasonably fast to load, but a bit slow to go from one page to another
Opera slow to load but a lot faster browsing
Dillo - lightning fast, but can't do anything with it;)  especially when most sites have frames

I'm trying to install OSB, but I'm stuck finding a package OSB-nrcore

Epiphany and Skipstone(?) I think are both mozilla derivatives, using Gecko(?) does this mean they will browse at the same speed as Firefox?

What do you all think?  Speed over functionality, but it must be able to handle frames and other basics...

---

### Post by cgjones on 2006-05-10
links, elinks, or lynx

---

### Post by mips on 2006-05-10
Try swiftfox (based on firefox) and install the fasterfox extension. You will be pleasantly suprised.

---

### Post by aysiu on 2006-05-10
I would use Epiphany.

---

### Post by treak007 on 2006-05-10
[QUOTE=damianubuntu]
Mozilla reasonably fast to load, but a bit slow to go from one page to another
..[/QUOTE]
Did you try mozilla suite or firefox, b/c if suite, firefox might be to your liking.

---

### Post by arsenic23 on 2006-05-10
Epiphany seems faster then firefox on my box.

Personally I think Opera and/or Epiphany are the two best browsers out there, and I use both, depending on what I'm up too.

---

### Post by Perfect Storm on 2006-05-10
My vote goes to Epiphany, before that I used firefox and it took some days to adjust, but now I'm totally hooked on it.

---

### Post by barbarian on 2006-05-10
For this machine, Opera probably best solution, IMHO

---

### Post by brady618 on 2006-05-10
I love Opera, been using it for a long time, and I recommend it to everyone.  I browse and get my email with it, and it is, in my opinion, by far the best.  Firefox is cool because you can get the "stumbleupon" extension, which is totally awesome, but I ONLY use Firefox for that.  I've never tried Epiphany, though, so I'll have to give it a whirl, see how it compares.

---

### Post by damianubuntu on 2006-05-10
Thanks everyone, thats all very interesting.

Now that I've got Dapper Xubuntu up and running, I'm trying Epiphany, seems pretty good so far.....

---

### Post by Sef on 2006-05-10
> For speed on a relatively low spec machine PII 500 ish with 256 ram


Epiphany would work best.  Another one to try would be galeon.  Both are lightweight browsers and are faster than firefox.

---

### Post by testube_babies on 2006-05-10
[QUOTE=mips]Try swiftfox (based on firefox) and install the fasterfox extension. You will be pleasantly suprised.[/QUOTE]

I thought SwiftFox was specifically built for AMD machines.  Am I wrong here?  Would it speed up my Pentium browsing?

---

### Post by CybaCowboy on 2006-05-10
I use Opera...

It's fast and secure, has a great user-interface, excellent features and best of all - it's named after me (my surname is Opera)!

lol

---

### Post by Stirling on 2006-05-11
[QUOTE=testube_babies]I thought SwiftFox was specifically built for AMD machines.  Am I wrong here?  Would it speed up my Pentium browsing?[/QUOTE]
There are now Intel builds also.

---

### Post by Clay85 on 2006-05-11
I love firefox. It does take a bit to load on my stupid machine. I've never tried anything else, but I've really really customized my Firefox -which is probably why it takes a few seconds to load. I have my weather, all of my GMail accounts, quick dictionary.com lookup, Wikipedia is one click away; all kinds of neat stuff. 

It's like an extension of me, really. It's become a necessity. I'm so lost in other browsers I had to load up Portable Firefox on my USB for use when not at home.

---

### Post by Ozitraveller on 2006-05-11
If you are using Xubuntu, then check the dependencies before installing Epiphany it uses a number of Gnome libraries!

---

### Post by Sef on 2006-05-11
>  	If you are using Xubuntu, then check the dependencies before installing Epiphany it uses a number of Gnome libraries!

Actually not too many.  

> sef@jokat1:~$ sudo apt-cache search epiphany
Password:
epiphany-browser - Intuitive GNOME web browser
epiphany-browser-dev - Development files for Epiphany web browser
epiphany-extensions - Extensions for Epiphany web browser
epiphany - Clone of BoulderDash Game
peercast-handlers - P2P audio and video streaming handlers


---

### Post by barbarian on 2006-05-11
Better to use: 
[I]sudo apt-cache **show** epiphany-browser
Package: epiphany-browser
Priority: optional
Section: gnome
Installed-Size: 9680
Maintainer: Jordi Mallach <jordi@debian.org>
Architecture: i386
Version: 1.9.6-0ubuntu1~ots1
Provides: www-browser
**Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libaudiofile0 (>= 0.2.3-4), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2), libdbus-1-1 (>= 0.36.2), libdbus-glib-1-1 (>= 0.36.2), libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.1), libgconf2-4 (>= 2.9), libgcrypt11, libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.8.0), libgnome-desktop-2 (>= 2.9.91), libgnome-keyring0 (>= 0.4.3), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.11.0), libgnomeprintui2.2-0 (>= 2.12.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.11.3), libgnutls11 (>= 1.0.16), libgpg-error0 (>= 1.0), libgtk2.0-0 (>= 2.8.0), libice6, libjpeg62, liblaunchpad-integration0 (>= 0.0patch26), liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.10.1), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6, libstartup-notification0 (>= 0.8-1), libstdc++6 (>= 4.0.1), libtasn1-2 (>= 0.2.8), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.20), libxrandr2, libxrender1, libxslt1.1 (>= 1.1.15), python2.4 (>= 2.3.90), zlib1g (>= 1:1.2.1), firefox, gnome-icon-theme (>= 2.9.90), iso-codes, gconf2 (>= 2.6.2-1)**
Recommends: yelp, epiphany-extensions, firefox-gnome-support
Conflicts: mozilla-browser (>= 2:1.8)
Filename: breezy/epiphany-browser_1.9.6-0ubuntu1~ots1_i386.deb
Size: 3479642[/I]
:D

---

### Post by Kobalt on 2006-05-11
Epiphany is defenetly good... Even though I'd recommand you Firefox, as said, Epiphany is really dependent on gnome libraries to work out of the box.

---

