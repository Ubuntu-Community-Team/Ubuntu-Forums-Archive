---
title: "Full install Ubuntu-Reverse"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-08
[COLOR="DarkRed"]Hello, since I have downloaded every media player and installed wine and I have no luck with getting my German programs to run, what about partitioning the drive to still run windows.  I did a full install though, total erase of Windows 2000 I believe it was but I had Windows XP over it.  I have one disk for XP only.  but I suppose several for the original dirvers.  I dont know the process to do this what-so-ever.  I would not do it if my games would run, but no luck all there.  How do I partition the drive to have Ununtu and XP, and in doing this what will I need to supply as far as drivers.  Also, is it by choice on the printer/scanner as to which window I use it in? Ubuntu or Windows XP ?   Thank you 

Sherri[/COLOR]

---

### Post by Ocxic on 2007-04-08
all you have to do is have one partiton for windows, and one for ubuntu.
the easiest way to do this would be to install, windows, only giving it half, of you hard drive or whatever you want, then you can use the rest when you setup ubuntu. make sure you install windows first, or else it'll screw up ubuntu.

doing this, you'll have to re-install both windows and ubuntu tho.

as for drivers, you'll just need the usually one for windows and ubuntu alike, nothing speacial needs to be installed.

---

### Post by mikewhatever on 2007-04-08
You can look at the guides of XP home/pro clean install here:
[http://theeldergeek.com/xp_home_install_-_graphic.htm](http://theeldergeek.com/xp_home_install_-_graphic.htm)
[http://theeldergeek.com/xp_pro_install_-_graphic.htm](http://theeldergeek.com/xp_pro_install_-_graphic.htm)
To partition your HDD use [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") or Ubuntu desktop cd which also has GParted.
The problem you will encounter after installing XP is that Windows boot loader ignores Linux, so, Ubuntu will be unbootable. Here is how to deal with it
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)
Another option would be to formate the HDD (loosing all data), install Windows leaving unallocated space for Ubuntu, and then install Ubuntu.

---

### Post by delilahjed44 on 2007-04-08
[QUOTE=Ocxic;2422134]all you have to do is have one partiton for windows, and one for ubuntu.
the easiest way to do this would be to install, windows, only giving it half, of you hard drive or whatever you want, then you can use the rest when you setup ubuntu. make sure you install windows first, or else it'll screw up ubuntu.

doing this, you'll have to re-install both windows and ubuntu tho.

as for drivers, you'll just need the usually one for windows and ubuntu alike, nothing speacial needs to be installed.[/QUOTE

Well hey thanks, I guess if I did a full in-stall with windows I can always go back and install ubuntu as partition when it ask, I think.. The other way for me will goof me up, and yes I do things the hard way first, ( sigh ) never learned differently.  Ok, well thank you 

Sherri

---

