---
title: "Installed Quanta and have encountered problems on starting it"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-08-18
Installed Quanta and have encountered problems on starting it. See image. If I click OK on that, another error message pops up saying something about configuration message not being writeable.... Finally got another popup, see second attachment.

Also, when I installed Quanta, it said it was for the KDE desktop environment. What is this? I'm using the standard Ubuntu desktop.....

Thx.

---

### Post by JerMe on 2006-08-18
Kubuntu uses KDE, Ubuntu uses GNOME.  KDE and GNONE are desktop managers, basically the look, feel, and organization of your GUI desktop.  If you look at screenshots of GNOME and KDE, you'll see the difference in layout.  It's a lot more than that, but you'll get the picture.

Anyways, Quanta is part of KDEWebDev, which is primarily made for KDE.  You can (supposedly) run Quanta in GNOME (Ubuntu), granted that you have all the KDE libraries installed.

I can't comment on the error you're getting.  You can, however, try another HTML editor named Bluefish:
[http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)
```
sudo apt-get install bluefish
```

---

### Post by zxee on 2006-08-18
Quanta is a web dev environment for KDE if you installed ubuntu you're using gnome. 
You can get kbuntu which has KDE as it's default window manager or if you have a fast internet connection you can use apt-get to install kde

Another option would be to look for a webdev/html editor that can be used in gnome-ubuntu's default window manager.
Bulefish is just such an ap [http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)

---

### Post by BlackMambo on 2006-08-19
nope - Bluefish isn't great, hence I need something else and Quanta was recommended.

---

### Post by eschatologicalhumor on 2007-03-25
I have successfully installed Quanta under the Gnome environment, although, only two of the plugins have their destinations validated, that is to say, Quanta can only find 2 of the plugins that were installed, although, ALL of the required plugins were infact installed during the quanta install. Quanta is looking for a /kde3 folder on my disk, when infact, it does not exist.

I tried uninstalling quanta:

> sudo apt-get remove quanta

then:

> sudo mkdir /kde3

hoping that since Quanta was looking for that folder, it would find it next time it installed. But no. Apparently, that folder is the default destination folder Quanta looks for, and KDE should already have those plugins' libraries installed pre-Quanta into that folder. 

So I then tried file searching for the plugins themselves, and only retrieved, for example: kfilereplace.desktop, instead of kfilereplace, even though my search query was for 'kfilereplace'. So there are now rogue programs/plugins on my disk that cannot be used because of the KDE/Gnome incompatibility, and while Quanta **does** work without those plugins being verified and available, I can see error messages, possibly even crash reports in my future. So I'll continue to use NVU and make up for the lack of features with code snippets off of the internet. :) 

You're on your own now buddy, as I am a lacky and require the WYSIWYG interface when building webpages. Good luck!

---

### Post by eschatologicalhumor on 2007-03-25
Also, if you're using the standard Ubuntu desktop, which means that GNOME is your GUI, why does that second attachment show KDE Krash Handler? Should be the GNOME crash handler.... What did you do to your system Mambo? Try to switch from gnome to KDE on Ubuntu? Or are you actually using Kubuntu?

---

### Post by eschatologicalhumor on 2007-03-25
UPDATE!!:

I found a nifty little command that show's you which directories on your computer can be cleaned, or deleted due to their obsol33teness, and in the process, found where the plugins that Quanta installs are located.

> They are located in:
 /.kde/share/apps/quanta
and
/.kde/share/apps

not /kde3 as I had originally thought. So if you want to run Quanta under GNOME, go into the plugin options in Quanta, and for all the one's with an X (you'll see what I mean), navigate to those folders and find the plugins so that you can take full advantage of Quanta under the GnomeGUI. Hope this helps someone!

---

