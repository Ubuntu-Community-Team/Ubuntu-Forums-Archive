---
title: "Issues with Edgy on Powerbook"
date: 2006-12-03
forum: Apple PPC Users
---

### Post by galvatron1983 on 2006-12-03
Ive had Edgy on my PowerBook for a couple of days now and everything is running fairly smoothly, it even suspends to RAM correctly when the lid is closed. But there a few things I need solving before I have the perfect Kubuntu set up. 

1) Java, and Flash. Is it true that these cant be installed on the PowerPC version of Unbuntu?

2) Brightness control. A bit of a silly one I know, but at the moment Im stuck on half brightness and I dont know how to increase/decrease it. I found a small app called pbbuttons, but when I downloaded it and tried to install it the package manager said I already had the latest version. How do I actually use pbbuttons?

3) Video/Audio codecs. A tip for anyone struggling to view any kind of video in Ubuntu PPC, download VLC, ran everything straight away, without the need to install any codecs. 

4) Airport Extreme, something that I need to get to work, Im going to RTFM that one.

---

### Post by AlphaMack on 2006-12-04
1.  Yes.

2.  Have you tried Fn+F1 or Fn+F2 by any chance?

3.  You can still install codecs following the Restricted Formats wiki page, although you obviously cannot install w32codecs, Flash, or Java.

4.  Just grab bcm43xx-fwcutter, network-manager-gnome, and the extracted AppleAirPort2 file.  See the wiki page for bcm43xx.  (Caveat:  No WPA if you use NM).

---

### Post by calum on 2006-12-07
You can get PPC Java 1.5 packages from IBM's website (forget where exactly, but you need to create a free account to download them).  Seems to work mostly fine in Ubuntu, apart from Java Web Start.

Of course, since Sun made Java open source last month, you can theoretically just build it yourself :)

---

### Post by hoyd on 2007-01-03
[http://joona.kuori.org/ubuntu-powerbook/](http://joona.kuori.org/ubuntu-powerbook/) is your guide to wireless and some other issues.

---

