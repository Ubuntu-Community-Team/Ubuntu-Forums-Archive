---
title: "I did it! And already a question....."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Talisker on 2006-08-04
No more Billy Gates.... ;) 

I finally installed Dapper on my Laptop and it installed flawlessly! Used Gpart to set the partitions and everything works... including Wifi.
Congratulations to the Ubuntu Team, a Job well done.

I have two questions just to start with:

1. I would like to copy the profil folder from Firefox (on Windows) and paste it into Firefox running on Dapper. Is that possible? I copied it already onto the Dapper desktop. I can't find the Firefox folder, tho.
Does anybody have an idea?

2. I used to have WPA-TKIP for my Wifi. I'm using now WEP 128-Bit in order to  set up Dapper. Can I configure Dapper to use WPA?

Thanks.

---

### Post by Christmas on 2006-08-04
I guess it should work. The default Firefox directory is ~/.mozilla/firefox this means in your home directory you have another directory .mozilla/firefox. Make sure to enable the view of the hidden files (CTRL+H in Nautilus? or alternately from one of the menus). Hidden files are the ones that begin with a dot.

---

### Post by Indras on 2006-08-04
1. Your firefox configuration files are stored in ~/.mozilla/firefox/  Just open your home folder (/home/<username>) in Nautilus and press Ctrl-H to bring up hidden files.  Look for the .mozilla folder then.  I'm not sure if the configuration files from the windows version are set up the same, someone else will have to confirm that.

2. I'm pretty sure you can, but I don't have a wireless card, so I've never monkeyed with it.  Do a search here in the forums for WPA, you should find a howto rather easily.

---

### Post by jimrz on 2006-08-04
#2- install network-manager + [COLOR="Red"]**gnome-network-manager**[/COLOR] (or kde has similar) from Synaptic it will handle that job + switching between wired/wifi + switching between various access points with different encryption methods quite nicely. You can search these forums and find several how-to's on the subject.

EDIT: OOOps..the correct package name = network-manager-gnome...sorry

---

### Post by Talisker on 2006-08-04
Thanks for the help, the hidden file thing got me. I copied the profile over and Firefox is doing fine.

Regarding the Wifi, thanks for the hint. I definitly gotta do the reading.

Great OS!

---

### Post by cheway on 2006-08-04
Apparrantly you will need network-manager and network-manager-gnome (this is the front end). However, I've been trying to get WPA working for ages now, and am having no luck whatsoever. I completely screwed my first installation commenting SOMETHING out (god knows what) - it was because I had no idea what I was doing (I still don't really lol), so be careful.

Best of luck to you.

---

