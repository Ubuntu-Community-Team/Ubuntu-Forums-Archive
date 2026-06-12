---
title: "Wine, Gecko IE, exe files"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Evelyn on 2007-09-17
I am trying to get a game from the internet and it saves it to my desktop as a setup.exe file.  I have downloaded Wine 0.9.45.  However it is not showing in my menu.  I have tried to open the exe file with Wine, but this messages "This product requires Internet Explorer 5.0 or higher."  So I went to the Wine HQ and learned that I could download Wine Gecko IE engine and down some stuff with regedit [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys).  I have tried everything (and hoping I haven't messed anything up)!  Please help!

---

### Post by Shazaam on 2007-09-17
My Wine install took a couple of reboots before it showed up in the menu. Did you do wincfg in a console and set up a fake Windows drive? And install the recommended Wine Windows packages using winetools?

---

### Post by Evelyn on 2007-09-17
How do I do that?

---

### Post by Billy_McBong on 2007-09-17
[COLOR="Blue"]how did you install wine?
if you installed it through synaptic it should be in in the application menu[/COLOR]

---

### Post by Evelyn on 2007-09-17
Yes I installed it through Synaptic Package Manager.  I had installed packages "wine" and "wine-dev", are there others I should have loaded?

---

### Post by Evelyn on 2007-09-17
Oh Please will someone help me!

---

### Post by Billy_McBong on 2007-09-17
[COLOR="Blue"]did IE install correctly?
and when you try to open the exe are you double clicking it or opening it through the terminal? you should use the terminal so if wine can display the errors[/COLOR]

---

### Post by Shazaam on 2007-09-17
Some old links that might help...
[http://ubuntuforums.org/showthread.php?t=149585&highlight=Wine+howto](http://ubuntuforums.org/showthread.php?t=149585&highlight=Wine+howto)
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main)

---

### Post by Evelyn on 2007-09-17
I assume that IE installed correctly because when I ran wine iexplore [http://www.winehq.org](http://www.winehq.org) an internet window shows up (but without a toolbar or menue).  When I try to open the exe I right click and go to Open with "wine".  I have also tried to open it in the terminal however it says that it can not be found.  I also tried to open in winefile the same error message appeared "This product requires Internet Explorer 5.0 or later."  And I still don't see it in the menu options after several restarts.

---

### Post by roidusoleil on 2007-09-22
The first thing you have to do after the wine installation is to invoke it from a shell window, for example with "wine --version". Then wine will realize, that no .wine directory has yet been created in your home directory and will accomplish this. Then, everytthing should work all right !

Regards

Kai

---

### Post by mysticmatrix on 2007-09-22
> **Evelyn said:**
> I am trying to get a game from the internet and it saves it to my desktop as a setup.exe file.  I have downloaded Wine 0.9.45.  However it is not showing in my menu.  I have tried to open the exe file with Wine, but this messages "This product requires Internet Explorer 5.0 or higher."  So I went to the Wine HQ and learned that I could download Wine Gecko IE engine and down some stuff with regedit [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys).  I have tried everything (and hoping I haven't messed anything up)!  Please help!

Can you tell us which game it is?

---

