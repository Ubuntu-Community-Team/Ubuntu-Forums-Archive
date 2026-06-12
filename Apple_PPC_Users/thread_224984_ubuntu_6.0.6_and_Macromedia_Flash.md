---
title: "ubuntu 6.0.6 and Macromedia Flash"
date: 2006-07-28
forum: Apple PPC Users
---

### Post by Lurcher on 2006-07-28
By the way, thanks to everyone who offered suggestions on how to install ubuntu on a iMac G3/500MHz.  After a little bit of trial and error, everything worked just fine.

That being said, on to the latest hurdle:  Some webpages require Macromedia Flash, but when I try to install the Linux version, using the command line, I get this message:  "Your architecture, \'ppc\', is not supported by Macromedia Flash Player installer."

OK, this would be less of an issue if it wasn't for the fact I cannot install the PPC version (that I am aware of, at any rate).  I also get the impression, from leading other posts that MMF is not available for ubuntu (which confuses me somewhat because the installer does say that it is for Linux, which ubuntu is just a version of).

Any help, suggestions, or verifications would be appreciated.

---

### Post by Jagot on 2006-07-29
Yeah, I'm afraid to say that Adobe do not produce Flash for the PPC architecture on Linux.  I've heard of some people using swf-player, so you may want to look into that.

---

### Post by N8K99 on 2006-07-29
I have tried and tried to compile Gnash for the PPC but am not having any luck getting it to run. Then I realized, I am not a huge fan of flash anyways - so I'll wait until something else happens.

---

### Post by kellogs on 2006-07-29
you could try to compile GNASH. Now swf-player, and all the other free flash projects has been unified into gnash. all the developers are looking into gnash development. it does work until flash version 7.0, and even some advanced features of flash 8 will be added. the bad/good thing is it does use OPENGL for rendering so If youve got no 3d acceleration you wont make it work. I compiled it fine but Ati support for ppc linux sucks... so I couldnt make it work because of opengl in my system.... but you could try.

this is the GNU central site of gnash:

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

and this is where you can report bugs, and get the latest CVS:

[http://savannah.gnu.org/projects/gnash/](http://savannah.gnu.org/projects/gnash/)

---

### Post by Lurcher on 2006-07-29
I hate to sound, well...geekish here, but it's kinda cool finding new (for me, at any rate) ways of doing already established things.

The rub is that it does mean that I ubuntu will probably not be my main system (that's what OS X is for) anytime soon, though I am learning quite a bit and expect that I will stay with ubuntu.

---

### Post by Lurcher on 2006-07-29
I also though that I would mention that ubuntu is so much easier to deal with with a four-button mouse, since I am not up to keyboard shortcuts with ubuntu yet.

---

### Post by FFred on 2006-07-30
The Flash player is compiled for x86 computers. Just like a PPC Mac OS binary won't run on an Intel Mac, a x86 Linux binary won't run on a PPC Linux system. 

Unfortunately for most commercial companies, Linux means "Linux running on a x86 based PC". This includes Adobe. Currently there are no binaries of the Flash player provided for non x86 computers running Linux. 

The only solution is to use an open source clone. However most Flash files won't play very well with those. 

(insert rant about clueless web developpers using flash for navigation and other silly things here)

---

### Post by printmkr on 2006-07-30
I wrote Adobe about getting a PPC version a couple of weeks ago, but never got any kind of reply. I guess with Apple going Intel, they figure the x86 version will be all anyone will ever need eventually.

---

### Post by marklid on 2006-07-30
> **printmkr said:**
> I wrote Adobe about getting a PPC version a couple of weeks ago, but never got any kind of reply. I guess with Apple going Intel, they figure the x86 version will be all anyone will ever need eventually.

Sad but probably very true :-(

---

### Post by FFred on 2006-07-30
There are several such apps, with two major ones from Adobe now : the Flash player and Acrobat reader. Although for casual use the FOSS PDF readers are usually pretty good now, you currently still need the Adobe one if you're going to have stuff printed, like when you work with Scribus. Lots of people have asked Adobe to provide non x86 Linux ports. So far no reply. Their /dev/null file must be getting huge by now.

Likewise I don't know what the situation is with the proprietary codecs on the Mac (i.e. is there a similar hack to using the Windows codecs on the x86 Linux - note that it doesn't work on 64bit builds).

All those problems exist on the "PC" systems too as soon as you stray from the path and try to build a 64 bit system for example. And of course if you run on one of the numerous other supported systems, Alpha, MIPS, SPARC, whatever, you're completely on your own as well.

---

