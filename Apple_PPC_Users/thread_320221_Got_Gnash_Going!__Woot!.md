---
title: "Got Gnash Going!  Woot!"
date: 2006-12-16
forum: Apple PPC Users
---

### Post by Gen2ly on 2006-12-16
I know some of you all  have got gnash to work, but I haven't been as lucky.  I was tired of compiling so I decided to wait until I saw it in the CVS.  Well guess what, I was trolling thru Synaptic and, voila baby, I saw it!  Yes, 0.7.2, may have been there awhile, but I don't regularly troll thru synaptic.  So I checked it, restarted el browsero, zzzzzzzz.  Wrong answer, Nothing.  I went thru 4 or 5 posts here in ubuntu forums and google for way to long.  I had given up when I made one last desperate try.  With gnash still installed run:
> sudo apt-get install libflash-mozplugin

Restarted the browser, actually I had to restart twice - it skizzed the first go round - and it worked.  Still don't see a plugin in my homefolder/.mozilla but it works.

I don't think I'll be going to shockwave.com anytime soon but at least it stops that annoying notice I see every time I cross a flash site.

OBTW, got the information at  [Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

I rule!

---

### Post by pay on 2006-12-17
You can alway test the plugin by going into Firefox and typing about:plugins in the address bar to verify that it installed.

---

### Post by magnolia fan on 2006-12-17
Me too!  Found it in Synaptic, installed and worked on the first try.  Wow, thanks for the tip.  MOL for remote OSX and OS9 desktops, Mplayer plug-in for Quicktime, and now Gnash for flash all in one day.  This has been one sweet day.

Edited to say that MOL is a remote desktop, not a virtual image of the Desktop.  Changes will be felt.

---

### Post by handylinux on 2006-12-17
> Found it in Synaptic ....

I'm new to this, maybe doing something wrong, but ... I can't find gnash in the Synaptic Package Manager. A search for "gnash" found nothing, a tedious scroll through the list went from "gnarwl" to "gnat".  So I tried installing "libflash-mozplugin" and now flash seems to be working (on a couple of webpages I checked). So "libflash-mozplugin" = gnash?

PS: Well, some flash ads work, anyway, like at [sourceforge.net]("http://sourceforge.net/") and [macworld.com]("http://www.macworld.com/"), but more demanding (?) flash stuff doesn't, like at this [film site]("http://naam.pair.com/aftf1626/AFTF/").

---

### Post by handylinux on 2006-12-17
Okay, so I finally figured out how to see which plugins are installed; the note above was a hint, but unfortunately this forum interprets certain letter combinations as code for smileys (I've run into this before), so I had to go to Firefox's help website and hunt around to find that it's simply about[colon]plugins. (If you enter colon+p you get a smiley: :p.)

So I see I have the following plugin installed:

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0
    GPLFLash homepage : gplflash.sf.net

So it appears this is what "libflash-mozplugin" installs: gplflash, not gnash. Which I guess is why I can get older, simpler flash content, but not newer, more demanding stuff.

A visit to the linked [GplFlash homepage]("http://http://gplflash.sourceforge.net") informs me that development has ceased on this utility, and refers me to [Gnash]("http://www.gnu.org/software/gnash/"). Which tells me that "Gnash releases can be found in the subdirectory /gnu/gnash/ on your favorite GNU mirror."

Isn't that what Synaptic does? But I still don't see gnash there, even after hitting Reload. Can anyone tell me where to find it?

---

### Post by pay on 2006-12-17
Try ```
sudo aptitude install cvs build-essential checkinstall automake autoconf libtool #the last 3 should be part of build-essential aswell
export CVS_RSH="ssh"
cvs -z3 -d:pserver:anonymous@cvs.sv.gnu.org:/sources/gnash co gnash
cd gnash
./autogen.sh
./configure --enable-plugin --with-plugindir=/usr/lib/mozilla-firefox
make CFLAGS=-O2 -g CXXFLAGS=-O2 -g
sudo make install #or if you want a deb sudo checkinstall
```

---

### Post by fuoco on 2006-12-18
there's no need for gplflasg or libflash at all.
gnash is now in edgy-backports. Just install the package 'mozilla-plugin-gnash' and that would pull all the needed dependencies, works out of the box for me. Even then it's still under development and many flash movies don't work right. That said it didn't crash on me once yet.
good luck.

---

### Post by handylinux on 2006-12-18
[QUOTE=]gnash is now in edgy-backports. Just install the package 'mozilla-plugin-gnash'....[/QUOTE]

What are "backports"? I hunted around for a while in Ubuntu Help, etc., but couldn't find anything about them. Finally did a search in Firefox's Search Bar "Ubuntu Package Search" for "backports", which found nothing, but gave me a link to the ["Ubuntu packages" page]("http://packages.ubuntu.com") where I found a link to "edgy-backports", where I found gnash under "all packages". Okay, it exists. (Still don't know what backports are, though.)

So I went back to Synaptic Package Manager / Settings / Repositories (Software Sources), and tried "Internet Updates", and there was "Backported Updates"; I checked it, reloaded the list in Synaptic Package Manager, and searched again for "gnash". Lo & behold, here it is. So I installed it (including noticed dependencies).

(So, **Dirk.R.Gently** and **magnolia fan**, did you have "Backported Updates" checked in Software Sources?)

Oops. Looked again, noticed it said "This package includes the standalone GTK+-based OpenGL player." Looked further down the list, saw "mozilla-plugin-gnash". Installed it. So I guess I have Gnash installed for Mozilla now, but it doesn't help with the movie site I linked above.

Just to be sure, I deleted "libflash-mozplugin". Now I have only Gnash installed. Still no movie clips. Well, kudos to the developers, and here's hoping Gnash eventually draws even with the commercial version.

---

### Post by Gen2ly on 2006-12-18
First of all, thanks Pay.  I did try your code and it almost worked.  I didn't have one thing correct and I was too tired last night to figure it out.  Oh, BTW, the -g flag wasn 't recognized.

fuoco, it's good you saw this post!  I had multiverse and restricted but I didn't know about the backports.  Feel a little bit silly actually. been searching all over the web and haven't got anything.  Unlucky I suppose.  I'm gonna give this a go...

--

Heeeeeyyyy!   It Works!  Thanks for the Assistance.

I removed flashplayer.xpt and libflashplayer.so from: usr/lib/firefox/plugins/libflash-mozplugin.so
though I'm not sure if it makes any difference.

---

### Post by johnrobert on 2006-12-28
I have gnash loaded now, using the deb package, but I can't find any flash that I can actually see with it. :-k   Can anyone point me to a url with some swfs that they've been able to see using gnash on the ppc?

---

### Post by wanger123 on 2006-12-31
Can anyone see youtube videos with this??

wanger

[EDIT:] I found this thread:[http://www.ubuntuforums.org/showthread.php?t=315438&highlight=youtube](http://www.ubuntuforums.org/showthread.php?t=315438&highlight=youtube) (thanks ssam) then downloaded 

the greasemonkey extension for firefox and then installed the yousabletube script from here: [http://userscripts.org/scripts/show/5906](http://userscripts.org/scripts/show/5906).

Now I can save vids directly to my hard drive and play them with mplayer. Very cool!!!!!!!!

wanger

---

### Post by fuoco on 2007-01-06
has anyone tried gnash cvs and can comment on improvements since the 0.7.2 release? thanks...

---

### Post by kellogs on 2007-01-12
there is a file called Changelog when you fetch gnash or any CVS/SVN file that you can read to see the last commited changes, you don't need to download anything if you only want to see the changes, just browse the cvs from your navigator. 

I Tested gnash ver. 0.7.1  , it worked quite well for banners and little flash effects but was a bit problematic with sites like miniclip or teagames (both sites with quite complex flash games) and no streaming movie support. Haven't tested the last cvs versions from two months or so but I heard they were implementing movie streams through Gstreamer and opengl. 

The developers of Gnash are quite active and very responsible, I had compile errors on the ppc and they fixed it in the same day, that is very respectful from their part and they are doing a very good work with flash, we cant say the same about the adobe flash ppc port :P

---

### Post by Uta on 2007-01-13
I successfully installed the flash plugin and the script that lets me download YouTube clips. The clips play prefectly with Kaffeine but with no sound? Is there a fix for this?

---

