---
title: "Bittorents?"
date: 2007-03-03
forum: Apple PPC Users
---

### Post by Clordio on 2007-03-03
Are there any bittorent applications for ppc linux?

---

### Post by teaker1s on 2007-03-03
have you enabled universe repositories and searched with synaptic?

---

### Post by Clordio on 2007-03-03
I actually havn't even installed it yet. See, I don't have the OSX cd and will have to do a clean install on my imac and I want to make sure that everything I need will be available before taking the plunge. I'll have to use the live cd to check in the universe rep. So is AAC supported with Gstreamer in ppc Ubuntu? So so many questions.

---

### Post by teaker1s on 2007-03-03
never using a mac
as long as you can boot kernel most 32bit packages should work, the packages in my sig don't have versions for different architectures on 32 bit. failing that you could compile:popcorn:

---

### Post by Clordio on 2007-03-03
Ok, thanks. hopefully this should all work out.

---

### Post by spikee on 2007-03-03
Check out Deluge torrent.
[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by 3rdalbum on 2007-03-03
> **teaker1s said:**
> never using a mac
as long as you can boot kernel most 32bit packages should work, the packages in my sig don't have versions for different architectures on 32 bit. failing that you could compile:popcorn:

I *believe* there is no AAC support for PowerPC; the other day I tried installing gtkpod-aac on Copland and got the message that the package didn't exist. But I could be wrong.

Yes, there are Bittorrent programs for PowerPC. The official BT client will work, as it's written in a cross-platform language. Ubuntu comes with gnome-bittorrent, and there are other clients available in the repositories. Unfortunately, Azeurus does not work yet.

Also, I'd just like to make a correction. Packages that are made for x86 Linux will *not* work on the PowerPC. If the source code for the program is available, chances are that you can compile it for PowerPC.

However, for closed-source programs like Flash and Skype, you should seek out free alternatives like Gnash and Ekiga. Unfortunately, Wine is also not available (as all Windows programs are written for x86).

---

