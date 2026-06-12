---
title: "Bittorrent of Hoary Array 5 or Array 6? Where?"
date: 2005-03-03
forum: Apple PPC Users
---

### Post by Thomas Ferreira on 2005-03-03
I found this web page.

[http://archive.ubuntulinux.org/cdimage/releases/hoary/array-6/](http://archive.ubuntulinux.org/cdimage/releases/hoary/array-6/)

But, no torrent starts to download as the file appears to have no peers.  If there is a PPC Torrent for Array 5 or 6, can someone point me in the right direction.  Hoary 3 and 4 would not either install or boot on my G5 so I want to try again with the most recent version.

Thanks

Thomas

---

### Post by toojays on 2005-03-04
Do you know about jigdo?

If you already have an Ubuntu CD, jigdo is probably a better option than bittorrent. It will look at your old CD or ISO, and then download only the packages it needs to make the new ISO. Very clever.

---

### Post by Thomas Ferreira on 2005-03-04
That sounds interesting but the CDs I have are the Warty 4.10, the Hoary Array 3 and 4.  None installed on my system and ran so how would these CDs I have already work in regards to that or does it not matter what version I have?

Thomas[

QUOTE=toojays]Do you know about jigdo?

If you already have an Ubuntu CD, jigdo is probably a better option than bittorrent. It will look at your old CD or ISO, and then download only the packages it needs to make the new ISO. Very clever.[/QUOTE]

---

### Post by toojays on 2005-03-04
The way it works is:

Install [Jigdo](http://atterer.net/jigdo/) on the computer you are doing the download from.

Get the [array 6 ppc jigdo file](http://cdimage.ubuntu.com/releases/hoary/array-6/hoary-install-powerpc.jigdo).

Run Jidgo on that file. When it asks for a CD, point it to the array 4 CD you already have. It will look at what files are on that CD, and only download the packages from Hoary which changed between array 4 and array 6.

I hope that explains it better; read the jidgo web site if you need to know more.

---

### Post by bored2k on 2005-03-04
wow i hav always re-DL the .isos, didnt even knew what jigdo waz

thnx a lot !

---

### Post by Viro on 2005-03-04
You could always just install Warty, and edit the /etc/apt/sources.list file and change all instances of Warty with Hoary. That'll give you a Hoary system.

---

