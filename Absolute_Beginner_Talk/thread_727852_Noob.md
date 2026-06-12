---
title: "Noob"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by shelbyoldsaurora on 2008-03-18
Just wanted to say hello.  I managed to get Ubuntu downloaded and installed.  Where do I go from here?  Looking forward to learning this new OS and hopefully get good at it.  Thanks in advance for all the help guys.

Changed the title per request

---

### Post by renzokuken on 2008-03-18
> **shelbyoldsaurora said:**
> Where do I go from here?

Hi shelby,

I guess it all depends what you want to do with your PC and your shiny new Ubuntu installation. Ubuntu can be as point-and-click easy or as commandline as you want. Maybe try learning some of the basic command line tools, which may (will) become very useful as you progress with Linux.

You could customise your desktop ( [www.gnome-look.org](www.gnome-look.org) ).....seriously, the possibilities are as endless or limited as you want to make them.

---

### Post by Boyohazard on 2008-03-18
Basically just start using it. If you're looking for some more specific steps try [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Have fun :)

---

### Post by mali2297 on 2008-03-18
When you are getting tired of changing your desktop themes...
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by hyper_ch on 2008-03-18
use next time a descriptive topic title and not a generic "noob here" or "help needed".

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by billgoldberg on 2008-03-18
you'll want to add the medibuntu repository to your system and add a few codecs/programs you will need.

Open up a terminal (applications -> accessories) and copy/paste

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Press enter.

Then this:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Press enter.

Then enter these commands (they will give you things like flash, java, video, dvd, audio, rar, ... support).

```
sudo apt-get install ubuntu-restricted-extras
``` (java, flash, windows fonts, ...)

```
sudo apt-get install vlc
``` (thats a media player that will play everything)

```
sudo apt-get install libdvdcss2
``` (dvd playback)

```
sudo apt-get install non-free-codecs
``` (win32 codecs, divx, ...)

```
sudo apt-get install p7zip-full
``` (zip, rar, 7zip, 7z, ... support)

(note: all these programs can be install using "system -> administration -> synaptic package manager", some can be install using "applications/add remove", but the terminal is faster)

---

### Post by housam on 2008-03-18
You may need to install some of [[COLOR="Red"]_these programs_[/COLOR]]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html").

---

### Post by nichpakaich on 2008-03-18
whoa .. I'm a noob, too. Didn't expect that any newbie would get this much support in a short time :)

You guys really did a great help, I'm new with my Kubuntu 7.10 over here. Still wandering all the net for any tips and info.

Great job guys, thanks.

---

### Post by shelbyoldsaurora on 2008-03-18
Wow thanks for the immediate responses.  Just getting my feet wet and ran into a hitch.  I tried opening our .mdb in open office.  I went to open existing database, found the file on our server, and clicked open.  It just locked up and I had to force quit openoffice.  Where am I going wrong?

---

### Post by forrestcupp on 2008-03-18
One good thing for a brand new user to do, is go to Add/Remove Programs in your main menu and browse through all of the thousands of programs you can freely download and install.

---

### Post by shelbyoldsaurora on 2008-03-18
Ok I found a solution: mdb tools.  I successfully installed this but where did it go?  OO still will not open an mdb file.  I'm sooooo confused.  It's not under the applications> office menu.  Heck, it's nowhere to be found.  Hopefully I'll be as smart as you guys one of these days

---

### Post by Fordkiller on 2008-03-18
Wow I have to say thanks alot I have been trying to get this stuff done myself by reading and doing and have gotten some but not all and just reading this post help me a ton again thanks a lot guys and gals for all the great help and posts

also i was a vista user but now i will only be a linux user and just use the post i found to make it look like vista :} again thanks a lot

---

