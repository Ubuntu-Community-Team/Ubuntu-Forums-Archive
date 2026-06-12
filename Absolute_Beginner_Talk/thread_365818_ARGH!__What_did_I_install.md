---
title: "ARGH!  What did I install?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-02-20
**Author's note**: This is a long boring essay trying to explain what I mean.  If you just want me to get to the point, scroll to the bottom of my post.



I've got a problem...  It's not a huge problem,  It's not really a "problem," in fact, but more of an inconvenience.

I am a Windows user using Linux.  I've been using Linux (various flavours) for about a year, now, and I'm currently on Ubuntu (Kubuntu to be exact) Edgy.  Even with using Linux all this time, though, I've still got a lot of Windows just ingrained into my mind.

One of the things I'm used to with Windows is knowing (well, for the most part) what I've installed on my computer.  It's almost always right in the Start Menu, and/or in the Add/Remove Programs menu.  On Linux, though, that's not always the case.  Sometimes, it goes into your K Menu (or whatever GNOME's equivalent is).  Sometimes it doesn't.  But it's THERE.  But sometimes you jsut forget it's there, because you don't see it.

For example, I recently installed ZSNES.  I would expect this to go in the Games category in my K Menu... but it doesn't.  I look through the menus for it, and can't find it (though I suprisingly find a Diablo II:LoD shortcut in my "Lost and Found" section, heh).

I don't know where zsnes is, but I know I can type "zsnes -?" to get help on how to run it from the terminal.  THat's good enough for me for that...  but what about other things?  I don't have a very good memory, but I don't want to have to tape a list of programs I've installed to the side of my monitor with descriptions of what they are and how to use them.

I know, a lot of you are probably saying, "don't install programs that you won't use, then."  Well...  Er... I will use them, eventually... maybe.  >.>  But it's kind of like I had this PHP Editor on my old Suse install that I hadn't used for like, four months, just because I forgot it was there.  Granted, I still think I would have liked Kate better, but I'm wondering what other things I might have installed and forgot about that I could have used.  In fact, I think I installed a metric butt-load of games that I'd only ever seen about half of, heh.





**THE POINT!**  The point is, can I make it, somehow, that all programs I install are SOMEWHERE in my K Menu?  Can I make a script, "sarteck-apt-get" or something, that will install the program AND link to it, if a link isn't made?  I know, it sounds pretty unreasonable, and I'm sure the answer is no, but I just wanted to ask.

Failing that, is there a way that I can see what I have installed and what I haven't?  I'm STILL learning the file structure, and all these names make little sense to me (I still say /usr as "user").  (BTW, is there an idiot's tutorial written in plain English that **can** teach me what /mnt, /dev, /usr, /etc, and all those other directories ARE for?  I really think that should be one of my first steps in getting to understand Linux better.)



Yes.  Now, somewhere in that mass of words I call "paragraphs" is a point.

---

### Post by FurryNemesis on 2007-02-20
I find it useful to keep a changelog in Tomboy or Stickynotes - not that useful, but you could always go to your home directory and hit ctrl+h, that'll give you all your hidden files and folders, which will for the most part be a list of the stuff you've got installed. Again, not very useful but I'd be interested in what other people suggest 

I bet there's a terminal command for this somewhere.

Anyone else?

---

### Post by Sarteck on 2007-02-20
> **FurryNemesis said:**
> I find it useful to keep a changelog in Tomboy or Stickynotes - not that useful, but you could always go to your home directory and hit ctrl+h, that'll give you all your hidden files and folders, which will for the most part be a list of the stuff you've got installed. Again, not very useful but I'd be interested in what other people suggest 

I bet there's a terminal command for this somewhere.

Anyone else?

Thanks Furry...  But I'll use old age as an excuse for not knowing what Tomboy and Stickynotes are (unless you meant actual sticky post-it notes, heh).  Are they some sort of program?

---

### Post by igknighted on 2007-02-20
> **Sarteck said:**
> Thanks Furry...  But I'll use old age as an excuse for not knowing what Tomboy and Stickynotes are (unless you meant actual sticky post-it notes, heh).  Are they some sort of program?

Yeah, those are programs that make little virtual sticky notes you can access on your screen.

To find a list of programs installed, most will be in these three folders: /usr/bin, /usr/local/bin, and /opt.  The two that end in bin are where most packages installed via apt will be.  Many third party programs get installed in /opt (like swiftfox, java from sun's site, the newest OO.o from their site, etc).  It is also possible for programs to install to your home folder.  These programs will only be available to the user whose home folder they are in.  To see the contents of these folders use the ls command.  Only the program binary will be in these folders, and in some cases it might not be easily recognized, but it's a place to start.

EDIT: as for packages installed via apt... synaptic can show you a list of all packages installed from the repo's.  This won't include anything not from the repo's however.

---

### Post by mahiyar on 2007-02-20
Two ways to know what programme you have installed 1) If you have installed through Synaptic then in Synaptic File -> History you will find your installed programmes 2) If through --sudo apt-get then running in a terminal >>cat /var/log/aptitude >>log.txt, then in gedit you can look at the file. For a good guide to linux try this [http://tldp.org/LDP/intro-linux/intro-linux.pdf](http://tldp.org/LDP/intro-linux/intro-linux.pdf) for a good guide to Ubuntu go here [https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html).

---

### Post by petri on 2007-02-20
Here is another file structure page [http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

And here is a couple of even "better" pages [http://psychocats.net/ubuntu](http://psychocats.net/ubuntu) and [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by ramjet_1953 on 2007-02-20
I don't use KDE, but under GNOME, I just note down the file's location and name of the application and then add it to the menu system, using System>Preferences>Alacarte Menu Editor.

Couldn't be easier!

Regards,
Roger :cool:

---

### Post by 3rdalbum on 2007-02-20
I keep a Tomboy page, but really; for the things that I install and they haven't put entries into my menus (lazy developers), I immediately go and add new menu items for them so I can't forget that they're there.

---

### Post by Sarteck on 2007-02-20
Oi, thank you all for the advice, and especially for the helpful links.  ^_^  Sorry, would have responded sooner, but I was reading from those links. XD

---

### Post by EtniesBMX on 2007-02-22
> **ramjet_1953 said:**
> I don't use KDE, but under GNOME, I just note down the file's location and name of the application and then add it to the menu system, using System>Preferences>Alacarte Menu Editor.

Couldn't be easier!

Regards,
Roger :cool:

Actually, I think it could be easier, especially when installing many applications. I too would like to see a feature that automatically adds installed programs into the KDE menu. 

By the way, a good application to see what programs you have installed is the **xfce4-appfinder **

---

### Post by jeffathehutt on 2007-02-22
You might also want to install the menu package.  The menu package installs the debian menu which would include many more installed programs than the plain default menus.

---

