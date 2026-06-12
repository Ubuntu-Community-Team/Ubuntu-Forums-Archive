---
title: "Flash(8) on PPC"
date: 2008-02-17
forum: Apple PPC Users
---

### Post by th0gersen on 2008-02-17
Hi, I'm trying to watch flash as a plugin in firefox on my ubuntu gutsy/ibookG4 ppc.
As a specific test case, say, i want the music player at [www.myspace.com/colafreaks](www.myspace.com/colafreaks). (It has swf8.)

- Tried gnash (mozilla-plugin-gnash). It does not support the flash 8 content on myspace. (although it can play youtube vids). So its _out_ of the question for now.
- swfdec was equally bad as gnash
- GPLFlash: No luck.
- Adobes flash (libflash-nonfree) is not supported on ppc.
- I also tried to use Adobe flash i386 (libflashplayer.so) via nspluginwrapper, but the installation did not succeed. nspluginwrapper got installed from src, but i ended up with an "*** NSPlugin Viewer *** preloader not found". I can post more details if needed.
[Dont know if qemu is necessary? Is there a guide?]

Is _anybody_ able to watch myspace flash (swf8) on ubuntu ppc???
Which route should I take to make it work?

Cheers, Martin

---

### Post by chipants on 2008-02-19
basically, i think you're outta luck for a native solution. gnash and swfdec won't play myspace videos. at least they never did when i tried. ndiswrapper does not include x86 emulation, as far as i know.

you've got two options, i suppose.

1) windows running in QEMU

2) mac os running in mac-on-linux

it doesn't seem like mac-on-linux has been maintained very well for quite some time. (somebody correct me if i'm wrong!) but, i used to use it quite extensively on a yellowdog linux machine. either way, i don't think anybody is maintaining a binary debian/ubuntu package for it. however, it is preferable to QEMU, if you can get it working. it will run os x (or os 9) pretty much as fast as they would run on their own.

[http://mac-on-linux.sourceforge.net/](http://mac-on-linux.sourceforge.net/)

---

### Post by th0gersen on 2008-02-20
> **chipants said:**
> 
...ndiswrapper does not include x86 emulation, as far as i know.

you've got two options, i suppose.
1) windows running in QEMU
2) mac os running in mac-on-linux


ndiswrapper? I guess you mean nspluginwrapper.

I think a full OS emulation is totally overkill to watch myspace video and I would prefer to avoid it. BTW, doesn't it mean that you have to buy a windows/OSX licence?

---

### Post by chipants on 2008-02-20
yes, i meant ndispluginwrapper. my fingers type quicker than my brain sometimes. errr. yes, that would mean that you have to buy a windows or mac os license.

sadly, adobe only puts out flash player for x86 linux. maybe one day gnash and swfdec will get good enough. i'm not horribly optimistic that will happen soon, though.

---

### Post by th0gersen on 2008-02-20
> **chipants said:**
> yes, i meant ndispluginwrapper. my fingers type quicker than my brain sometimes.

LOL! :) Certainly in this case. Guess you still mean nspluginwrapper ;-D Your fingers must be really fast! [ns=netscape. The project obviously started many years ago...]

---

### Post by chipants on 2008-02-20
> **th0gersen said:**
> LOL! :) Certainly in this case. Guess you still mean nspluginwrapper ;-D Your fingers must be really fast! [ns=netscape. The project obviously started many years ago...]

okay, that time i was just being dumb. like, when you are looking at something and accidentally say what you were looking at instead of what you meant. oh, goodness... that happens to everybody, right? ugh. . i think i hadn't had my coffee yet. grrr.

i amaze myself with my oblivion, on occasion.

---

