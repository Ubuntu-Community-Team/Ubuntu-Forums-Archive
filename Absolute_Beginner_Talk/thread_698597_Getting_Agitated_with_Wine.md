---
title: "Getting Agitated with Wine"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-16
Alright, so in a vain attempt to get Halo working, I've somehow completely messed up Wine. From the main menu, it shows the Wine folder, but when I go to it, the only thing listed is Programs-> Microsoft Games -> Halo. It doesn't show the Browse C: folder, or the Configure Wine either. When I uninstalled Wine, the folder and such are still there. I then probably made the mistake of reinstalling over a bad copy and now it won't access anything. Could someone help me completely delete out Wine and all of its folders, along with Halo residuals? I've got the .deb file for Wine 0.9.39 on my desktop, hoping to run off of that to get Halo working.

---

### Post by PurposeOfReason on 2008-02-16
Run this command to delete the .wine folder and all the settings. Then run the second to purge wine

 rm -rf ~/.wine 
sudo aptitude purge wine

Reinstall wine.

---

### Post by spacefreak86 on 2008-02-16
Alright, done, but Wine is still showing only that one folder on the main menu. Also, I re-installed it and went to the home folder, entered in ~/.wine to get to the wine folder. It claims that the folder does not exist.

---

### Post by magicman5421 on 2008-02-16
That happened to me too when I uninstalled Wine. I don't think it does anything, i think it's just residual and the purge doesn't get rid of it. Just go to System>Preferences>Main Menu and delete the Wine folder.

---

### Post by spacefreak86 on 2008-02-16
OKay, I sorta got it to work after a lot of installing / reinstalling. Question though. Is it possible to have Ubuntu run a program to emulate Debian, then have Debian run Halo? If so, how?

---

### Post by PurposeOfReason on 2008-02-16
Why do you want to emulate Debian? That would just take more resources. You could do it in virtualbox if you want.

---

### Post by spacefreak86 on 2008-02-16
Virtualbox? What and where is it?

---

### Post by PurposeOfReason on 2008-02-16
> **spacefreak86 said:**
> Virtualbox? What and where is it?
I still don't see why you want it. You're going to be running a game through wine in a virtual destkop in your actual desktop. It's a waste of resources. 
[http://www.virtualbox.org/](http://www.virtualbox.org/)

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

EDIT - Reading above you want to **emulate** debian. Why? Ubuntu is debian based.

---

### Post by spacefreak86 on 2008-02-16
I had read somewhere that Wine doesn't run Halo beyond 0.9.39, but Debian still ran. I was hoping to run an emulator through to be able to get Halo to work that way. I can get it to install, but I can't get it to run at all, but yet I've heard of others being able to run it. Halo is the last piece of software that is still tying me to XP.

---

### Post by JoshuaRL on 2008-02-16
If you just want that, then uninstall the Wine you have now.  Then go to their site and download the older version according to their directions.

---

### Post by spacefreak86 on 2008-02-16
Yeah, no dice. It froze up on install of "Creating Game Folders" in Wine 0.9.39, and while I got it to install on 0.9.41, the game won't load, where it gives me white boxes again where the buttons for Campaign, Multiplayer, Settings, Credits, and Quit are supposed to be. I don't even hear the background music, which is a bit unusual.

---

### Post by JoshuaRL on 2008-02-17
Try uninstalling Wine again, this time with Synaptic and make sure it has complete removal.  Then install it again and see what happens.

---

### Post by spacefreak86 on 2008-02-17
Okay, I got that done. I'm now running it on Wine 0.9.41, the last one that I read would still support Halo. I'm also running Gusty if that makes a difference. These are screenshots of what happens when I load Halo: (using no cd crack, Halo updated through Wine, and game installed)

[IMG]http://i29.photobucket.com/albums/c268/bdizzle86/Screenshot.png[/IMG]

Which then loads to this:

[IMG]http://i29.photobucket.com/albums/c268/bdizzle86/Screenshot-1.png[/IMG]

I have the launcher set as: env WINEPREFIX="/home/bdizzle86/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" -novideo

---

### Post by JoshuaRL on 2008-02-17
Can't see those.  When posting, go to the bottom and the button Manage Attachments.  You can attach them that way.

---

### Post by spacefreak86 on 2008-02-17
Updated picture files.

---

### Post by JoshuaRL on 2008-02-17
What happens when you try to run it through wine in the terminal?  It should spit out any errors there.

---

### Post by spacefreak86 on 2008-02-17
I tried to post it on here, but it says that I tried to put in 168 images...?

Anyway, I get the following error from the Wine screen with Halo: Cannot find Z:\home\user\config.txt

---

