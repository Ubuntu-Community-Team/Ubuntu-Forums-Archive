---
title: "Wireless config"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2006-02-06
In the wireless database ([https://wiki.ubuntu.com/HardwareSupp...ssNetworkCards](https://wiki.ubuntu.com/HardwareSupp...ssNetworkCards))
 it says "Works in Breezy (just configure it from the gnome network config tool), though it isn't recognized durring installation" for my card.  I went to Network tools under system tools and didn't see anywhere where I could configure it, it only had ethernet and loopback, no Add or Remove properties like in some of the screenshots. None of the other applications in my menus allow me to configure a wireless card and I was just wondering where that gnome network config tool was.

Thanks,
Nolan

---

### Post by gsdefender on 2006-02-07
The directions are right, but you may need to load the module as so before trying to configure the board:

# sudo modprobe [modulename]

as the configurator is not able to do this for you (I learnt it at my expenses :-D)

I am also assuming that you don't need any Windows driver (ndiswrapper, I mean) to do the job.

---

### Post by madddonkey255 on 2006-02-07
Thanks but how do I know what modulename to use.  I have a Marvell W8300 chipset, but I don't know what that means.

---

### Post by gsdefender on 2006-02-21
I'm sorry you need (as I need) to use ndiswrapper:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List0to9AtoH](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List0to9AtoH)

lists the chipset you have as in need for Windows drivers (search entry number 30 or so).

This article on the Ubuntu wiki

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

will tell you what you need to know if you've never used ndiswrapper before.
(so the infamous [modulename] will then become ndiswrapper ;) )

Hope this helps, and sorry for the delay.

---

