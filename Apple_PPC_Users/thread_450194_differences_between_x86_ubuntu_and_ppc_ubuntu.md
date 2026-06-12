---
title: "differences between x86 ubuntu and ppc ubuntu?"
date: 2007-05-21
forum: Apple PPC Users
---

### Post by tr333 on 2007-05-21
Hi,

I was looking at installing ubuntu on my old ppc powerbook and was wondering what the differences between x86 ubuntu and ppc ubuntu are?  I noticed that Medibuntu now provides packages for w32codecs on ppc (ppc-codecs) and libdvdcss2.  The only difference i notice is the lack of an official Flash Player, but I could probably get by with gnash or similar.

---

### Post by ruy_lopez on 2007-05-21
Gnash is a disaster, I found it spitting out sensitive information onto the flash applet (lines of code I'd typed half an hour before).

The main thing to remember with PowerPc is that it is being supported less and less these days. Things are only going to get worse. At the moment it isn't too bad. With the exception of flash and real player and things like that, it's almost identical to x86.

If you have an old powerpc machine, why not use it? Just be aware that powerpc is being cornered out of the market since Apple switched to Intel.

---

### Post by 3rdalbum on 2007-05-21
PPC-codecs isn't actually w32codecs for PPC; it's a different set of codecs.

Who needs Flash? Youtube videos can be downloaded regardless using Firefox extensions.

Another difference is that it's easy to find precompiled .debs for Ubuntu x86, but difficult to find the same things for PPC. On PowerPC, you find you have to either stick to the repositories or compile from source. Some things, like the Medibuntu stuff, Realplayer and Opera, are distributed as pre-compiled for PPC too though, which is great.

Tr333, I'd appreciate it if you could download Copland PPC some time as well and give that a whirl. It's got some "batteries included" and a lot of room to improve. I could do with some bug testers too :-)

---

### Post by tr333 on 2007-05-21
CoplandPPC looks interesting :)
is it compatible with the feisty repositories?

i will give it a try when i can manage to resize the main hfs+ partition that has osx installed on it.  i can't seem to find any free tools that will do it without losing any data ("diskutil resizeVolume" requires GPT partition format which ppc macs dont have).  i looked at using the pdisk commandline utility, but can't work out how to use it (it looks more complex than learning assembler :O).  currently downloading the gentoo ultimate cd as i read that the version of "parted" on it can shrink hfs+ partitions without data loss.


btw, you should change ur sig. to include a link to copland download.

---

### Post by tr333 on 2007-05-21
downloading copland at the moment :p, but it will be another 22 hours before it finishes :)
i would offer to help with code, but all i can offer is perl :p (probably not very useful for this sort of stuff).

---

### Post by stmiller on 2007-05-21
PPC Linux cannot execute x86 code- so no wine, ndiswrapper, or vmware.

And gnash is working on getting youtube video in the browser. There are current workarounds to view youtube (see PPCFAQs below).

And 3D driver support is okay, but not fantastic.

Linux runs wonderfully on PPC hardware, other than those things above.

---

### Post by 3rdalbum on 2007-05-22
tr333: Try the torrent:

[http://www.linuxtracker.org/torrents-details.php?id=4146]("http://www.linuxtracker.org/torrents-details.php?id=4146")

Copland is a Live CD, so you can try it out without repartitioning. In fact, I've not even tried installing it (too little memory in my test machine). Copland currently uses the Edgy repositories.

---

### Post by tr333 on 2007-05-23
> **3rdalbum said:**
> tr333: Try the torrent:

[http://www.linuxtracker.org/torrents-details.php?id=4146]("http://www.linuxtracker.org/torrents-details.php?id=4146")

Copland is a Live CD, so you can try it out without repartitioning. In fact, I've not even tried installing it (too little memory in my test machine). Copland currently uses the Edgy repositories.

Just finished the download now :)
Thanks for the info on the livecd.

---

