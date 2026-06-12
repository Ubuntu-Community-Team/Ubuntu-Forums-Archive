---
title: "A Few Questiona about WINE and uprading to Breezy..."
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by xUNDEROATHx21 on 2006-04-09
I just recently installed one of my old Ubuntu 5.04 CDs and I have a few questions...

First, I was wondeing how I would go about installing WINE. I followed the instructions stated in the wiki, by enabling the repositories...and then I rigth clciked on libwine and I got this message...And now I dont know what to do...

[I]libwine:
 Depends: wine  but it is not installable[/I]

I also have a question about the recent 5.10 release of Breezy, and I was wondering how I can upgrade my 5.04 release to that version...

thanks, much appriciated...

---

### Post by xUNDEROATHx21 on 2006-04-09
Oh, I was also wondering. I didnt install any drivers since the install...Do I need ATI/VIA/Audigy drivers for Linux?

Heres my specs...

AMD 64 3200(2.2GHZ)
Asus A8V Deluxe
ATI 9800PRO
2GB RAM
Audigy 2 ZS "GAMER"

---

### Post by Sutekh on 2006-04-09
> **xUNDEROATHx21]
First, I was wondeing how I would go about installing WINE. I followed the instructions stated in the wiki, by enabling the repositories...and then I rigth clciked on libwine and I got this message...And now I dont know what to do...
[/quote]
Try this...

- Open a terminal window (from the Menu said:**
> Wine Application Database[/url] to see how particular applications/games run with wine and any issues that you may encounter trying to get them working.


[QUOTE=xUNDEROATHx21]
I also have a question about the recent 5.10 release of Breezy, and I was wondering how I can upgrade my 5.04 release to that version...

thanks, much appriciated...
 - To do this you need to edit your sources.list again.  This time wherever you see a repository that contains **hoary**, for example
```
deb http://archive.ubuntu.com/ubuntu **hoary** main restricted
```
change it to **breezy**
```
deb http://archive.ubuntu.com/ubuntu **breezy** main restricted
```
 - Save the file and then refresh the repositories, then perform the dist-upgrade command.  This command will update Hoary to Breezy
```
sudo apt-get update
sudo apt-get dist-upgrade
```
 - Then it will begin dowloading *alot* of packages, to turn Hoary into Breezy


[QUOTE=xUNDEROATHx21]
Oh, I was also wondering. I didnt install any drivers since the install...Do I need ATI/VIA/Audigy drivers for Linux?[/quote]
 - You should look into this link for installing a driver for your ATI card.

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

 - There are others that you can look at by searching the forum.

 - If you plan on upgrading to Breezy (highly recommended), then wait until that's done before trying to install the AI drivers this way.

 - As for the Audigy, Breezy should be able to handle that for you.  In case it doesn't, post back.


 - Good Luck!

---

### Post by xUNDEROATHx21 on 2006-04-10
ok, I upgraded to Breezy, and its awesome...Thank you very much!

However, I still am unable to get Wine lo install, and to get my Audigy card working in Ubuntu...

That, and I need to find a way to get my wireless card(Dlink G510) working as well as QT/flas plugins, but thats what googles for....:)

Im on my windows partition just doing some stuff in Drmwvr/Photoshop, but soon ill log back into Ubuntu and play around some more...

---

