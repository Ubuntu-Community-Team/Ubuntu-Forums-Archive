---
title: "Flash and Ndiswrapper"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by wtfitsRICK on 2008-01-31
Okay.  My first major problem is with my wired connection.  When I'm connected, most things work fine.  Except one huge problem: flash (could be other things/plugins, but i don't know).  When I go to a simple site with flash (purevolume.com/thecolorfred), it flips out.  It acts like I'm clicking back and forth between the album and other tabs and stuff.  It does the same kind of thing on MySpace.  Any suggestions?  ::EDIT:: I checked some flash sites, and they're messed up too.  No sound from them at all.

Other question, I'm sure it's been answered multiple times, but how do I install the Ndiswrapper thing?  I downloaded the folder and stuff, but I have NO idea how to get it to work.  I'm very new to Ubuntu, so be gentle.  If such a thing exists, an install pack would be rad.  Otherwise, try to make it easy.  I have a Compaq Presario C700 laptop.

Thanks.

---

### Post by Flyingjester on 2008-01-31
i've never used ndiswrapper so i can't help you with taht unfortunately, but for flash go to adobe.com download the flashplayer and follow the instructions on the website, if for some reason you run into problems post it here and i'll help you.

---

### Post by wtfitsRICK on 2008-01-31
Okay.  I'm not used to the terminal much.  So, on there it says to navigate to the folder, and then do some install thing.

I don't know how to navigate to the folder in the terminal.  That doesn't help.  If you can tell me how to do that, I'd be happy.

---

### Post by Flyingjester on 2008-01-31
sure no problem let say you downloaded it to your desktop in terminal type : cd ~/Desktop/"name of folder without the quotation marks" then hit enter, then continue with the directions.

---

### Post by Flyingjester on 2008-01-31
cd ~/Desktop/install_flash_player_9_linux

and then 

./flashplayer-installer

---

### Post by DarkOx on 2008-01-31
If you go to Synaptic (or Adept, if you're using Kubuntu), you can search for a package called "flashplugin-nonfree" and install that. This'll give you flash. 

As for Ndiswrapper, this can get a bit more complex. It was definitely the most intimidating thing about Ubuntu when I first switched. Using Synaptic, install the package "ndiswrapper-utils". You should now be able to use Ndiswrapper from the command line. You need the driver files that came with your card. They can be found either on the vendor's website or on the CD that came with the card. You're looking for two files ending in .inf  and in .sys Once you've found the files, copy them somewhere convenient, like your desktop.

You could try installing a package called "ndisgtk", which I'm told is a graphical font-end for using ndiswrapper. I've never used it myself though. If you'd rather not try it, you'll have to use the command line instructions below.

Start up a terminal. If you're using Gnome, this can be found by going to &#8220;Applications&#8221;, then &#8220;System tools&#8221; and selecting &#8220;terminal&#8221;. In KDE, select the menu, then &#8220;system&#8221; and &#8220;konsole&#8221;.

From the terminal type:

cd /path/to/the/files. If you've saved the files to your desktop, this'll probably be /home/<username>/Desktop.

Then type:

sudo ndiswrapper -i filename.inf

replacing &#8220;filename&#8221; with whatever the relevant .inf file is called. If all goes well, the drivers should be installed. To check, type

ndiswrapper -l

This should return something like: filename          driver present, hardware present
if it does, it's safe to proceed. Type:

sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

To start ndiswrapper at every boot, you must modify the modules file. If you're using Gnome, type:

sudo gedit /etc/modules

Or, if you're using KDE type

sudo kwrite /etc/modules

either way, a text editor should pop up. Simply add &#8220;ndiswrapper&#8221; to the bottom of the file, save, and exit the program. Ndiswrapper should now load automatically at boot time.

That's it. Reboot your computer and your wireless should be working fine.

---

### Post by Flyingjester on 2008-01-31
yea, only reason i told him to go the adobe way is i'm not sure if they've fixed the synaptic flash bug yet, every time i tried to install it that way it kept saying it installed it, but mozilla kept requesting the plug in.

---

### Post by RomeReactor on 2008-01-31
Hi. The easier way to install Flash is to download one of these .deb packages:

* [flashplayer-nonfree 32-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")
* [flashplayer-nonfree 64-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466")

Close Firefox, and double-click on the package to install. More about the bug in flashplayer-nonfree from the repositories [here]("http://ubuntuforums.org/showthread.php?t=636397").

As for the problem with the sites, it sounds like the OP is using Gnash instead of Flash. Can you post a screenshot of the pages showing the problem? If you want to install Flash, make sure Gnash is uninstalled: go to 'System->Administration->Synaptic', search for Gnash, right-click on it and mark it for **Complete Removal**; or open a terminal (Applications->Accessories->Terminal) and write or paste:
```
sudo aptitude remove --purge gnash mozilla-plugin-gnash
```

---

### Post by o.besner on 2008-01-31
You can install Ndiswrapper with the "Add/Remove Programs" in the Applications menu. Just search for "ndiswrapper" in the search bar and you'll find it. Once installed, you can find it in "Administration" --> " Windows Wireless Driver". It has a graphic interface, so it's pretty straightforward. Just tell him where your driver is !

Good luck !

---

### Post by Kilz on 2008-01-31
If you are a 64bit user you might want to [visit this sticky]("http://ubuntuforums.org/showthread.php?t=476924") for Flash.

---

### Post by wtfitsRICK on 2008-02-08
Thanks, everybody.  When I'm back at a wired connection, I'll step over to Ubuntu and see if any of this works for me.  Hopefully, it will.  :D

---

