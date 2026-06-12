---
title: "What fonts are safe to delete?"
date: 2007-02-10
forum: Art &amp; Design
---

### Post by Gotou on 2007-02-10
I want to be able to add/remove fonts as I need to.  I do design work and juggling fonts fast and efficiently is a must.

Defoma will not do the job I need.

Fontlinge requires too much to setup and too much to maintain just to view the fonts.  I made it through to the last steps but Fontlinge seems too far out of date to work with Ubuntu.

There are a bunch of fonts on my Ubuntu (Edgy) system that I want to get rid of and others that I want to add.

Different font directories seem to be scattered all throughout the file system.  A few fonts are good but most are junk (at least for my purposes).

The .fonts directory in my home folder is currently empty.  I've read that it is possible to copy/paste individual fonts in and out of ~/.fonts as well as multiple folders that group fonts together.

/usr/share/fonts has:
directories:
afms (44 items)
truetype (807 items)
type1  (184 items)
X11  (1329 items)

and these files:
adobe-urw.font
debian.font
fonts.cache-1
groff.font
tex.font
urw-urw.font
X.font

I use Gnome, GIMP, InkScape and OpenOffice where fonts are a concern.

I've already backed-up the /usr/share/fonts to a safe place.

So, what fonts can I delete without fubaring my system?

Thanks!

---

### Post by hugmenot on 2007-02-11
I would approach this by looking at font packages first. In the past I used to remove all the asian scripts because I saw little use in them and they cluttered my font menus. Now I like the fact can I never see empty box substitute symbols on websites.
Check all packages beginning with ttf- in synaptic, you might want to uninstall those first.
Dropping files into ~/.fonts works flawlessly. You can make subdirectories to keep it organized.

---

### Post by Gotou on 2007-02-11
Thnaks hugmenot.

I used Synaptic to remove some fonts.  Got over-zealous and removed some that took GIMP and few other programs with them.

Ugghh!!!  #-o

Experience has taught me to use "remove" instead of "remove completely" so I was able to put things back.

Here's a wishful thought that applies to all OS's:
Programs that use multiple fonts, for the user to choose from, usually install their own as part and parcel.  If you use a couple of these programs they add to each other's font lists.  Several of these fonts look so similar that it's not worth having them listed (at least for me).

Why not create these programs so user has the ability to choose which fonts they want to have visible in that particular program's font list.  Something in the "Options" that would list all the fonts available with a check box next to each font to toggle them on or off.

Just wishful thinking. :roll:

---

### Post by nalioth on 2007-02-11
Yes, if whatever file you are contemplating removing is NOT in your home directory, leave it alone.

" Stay out of the system space. "  << this means anywhere outside of your home directory.

You can add fonts, as mentioned, into your ~/.fonts directory as needed.

---

### Post by hugmenot on 2007-02-12
Perhaps the lesson here is that you should always pay attention to what packages are going to be removed. Synaptic has surely warned you about it.

One package that is almost always removed is ubuntu-desktop, which means that you might miss some packages that ubuntu developers deem necessary for the desktop on the next upgrade, because they list these packages in ubuntu-desktop, so they get installed with it.

---

### Post by Gotou on 2007-02-13
Yup, I reinstalled ubuntu-desktop and it put back a bunch of fonts in various languages I can't speak or read.  <sigh>

---

### Post by Unterseeboot_234 on 2007-02-16
From a designer viewpoint, when you have to have "font sets" I like a little program called fonty python. Here was my link in the forums about fonty.

**[fonty python]("http://www.ubuntuforums.org/showthread.php?t=328950")**

---

### Post by anroy on 2007-02-19
In Abiword and OpenOffice, I hardly have any Western fonts, or at least the ones I am familiar with like Arial, Bookman, Century, Times New Roman and Verdana.  Yet there is a very large number of Indian and Middle Eastern fonts.

I never asked for this, it is ridiculous  (BTW my background is Indian, in case I'm sounding racist)

When I try to remove them from Synaptic I see that it also flags the package "ubuntu-desktop" for removal.  This is worrisome so I don't proceed.

What is this "ubuntu-desktop"?  Maybe it is the program that displays the desktop?  Why is it dependent on Indian fonts?

I really want to remove them because there are SO many of them they clutter up my font menus, and many of them have unattractive names, starting with lower-case "ae_" with underlines, etc.  It looks very sloppy.

And I want to get my usual Western fonts in there.

Does anyone have any idea what is going on and how I can rectify this.

Thanks!

---

### Post by hugmenot on 2007-02-19
To put it simply ubuntu-desktop is the plastic bag that holds all packages that comprise the Ubuntu distribution for desktop PCs.
In reality it is just a list of packages (so called dependencies; making ubuntu-desktop a meta-package).

Minimal example:

-  ubuntu-desktop
     depends on
        browser
        office
        music player
        stuff
        more stuff
        ...
        indic fonts
        malay fonts
        ...
       

To get something the Ubuntu developers want on a desktop system installed they just list it in ubuntu-desktop and increase its version number. On the next upgrade the new version will get installed and pulls in all new dependencies. (BTW, there&#8217;s also ubuntu-minimal, -server, etc.)
Now, if you uninstall "stuff" or "indic fonts"  then ubuntu-desktop cannot be satisfied anymore and wants to be removed. You can allow it but the next time Ubuntu developers want to add something to the desktop you will not notice because ubuntu-desktop is gone and will not be upgraded to pull the new stuff (as in "not previously installed") in with it.

I don&#8217;t habe ubuntu-desktop installed. How do I keep up with changes? I just periodically check what ubntu-desktop now depends on and then decide whther I want it too. Often I don&#8217;t (I&#8217;m not disabled so I don&#8217;t need accessibility packages, for example). All the packages that are already installed get upgraded by themselves of course.

---

