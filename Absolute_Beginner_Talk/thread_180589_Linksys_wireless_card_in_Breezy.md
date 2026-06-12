---
title: "Linksys wireless card in Breezy"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by bakumatsu on 2006-05-22
I have no idea where to start, I have a linksys wireless card and it won't work. I've heard that there's some issue with linksys and linux and you have to run some sort of wrapper or a windows emulator to get the drivers to work. But I don't know how to do that. Can someone please help?

---

### Post by vayde on 2006-05-22
you need ndiswrapper.  Fear not, it's pretty straight forward.

check out:
 [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

There is specific information on how to get your card working, but I don't know where it is off the top of my head.  Ill edit this and add it when I find it.

Here it is:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Depending on your experience, you should have all you need.  If you need more info, just holler.

---

### Post by damianubuntu on 2006-05-22
Hi,
try this troubleshooting page for a start:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

also follow the links on that page to see if your device is supported, particularly

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

and

[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

This should get you started at least.  Post back here if you have problems, but it might be useful if you could specify what card or device you are using!

According to some authorities here, NdisWrapper which allows you to use Windows drivers should only be used as a last resort.  Try and get the native support working first.

(no disrespect to Vayde ;-))
Cheers and good luck

---

### Post by vayde on 2006-05-22
[QUOTE=damianubuntu]

According to some authorities here, NdisWrapper which allows you to use Windows drivers should only be used as a last resort.  Try and get the native support working first.

(no disrespect to Vayde ;-))
Cheers and good luck[/QUOTE]

None taken.  god forbid that I lead anyone into temptation:D

---

