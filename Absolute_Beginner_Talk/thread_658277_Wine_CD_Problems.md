---
title: "Wine CD Problems"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-04
I'm trying to install warcraft 3 on my computer using wine.  The installation all went well, but upon trying to launch the program, my computer fails to acknowledge that the CD is in there.  The CD isn't terribly scratched, and it was clean enough to get an installation off of, and on top of that I did polish it up a bit with my shirt.  However, after trying to reboot, and put it back in several times, i still get the same error:

"Warcraft was unable to locate your Cd-Rom drive
Please make sure that warcraft is in your cd-rom drive, then click on retry"

Any ideas why it's not recognizing my CD?

---

### Post by lgambett on 2008-01-04
Check mappings in winecfg, e.g. launch winecfg in a terminal and check under "Labels" folder..

---

### Post by jordank on 2008-01-04
I'm not seeing any labels tab?

Am I in the right place? And what do i do when I find this labels tab?

Check the screenshot.

---

### Post by jordank on 2008-01-04
What else could this be caused by?  Does wine not know where to look for the cd?

---

### Post by sirgogo on 2008-01-04
jordank:

Wine is pretty awesome and all, but honestly its not quite ready for use with all games, Warcraft 3 being an example. I also have Wc3 installed, but launching the game is tough. The reason for this (as far as I know) is because Wc3 checks for copied and burned disks using a executable that works on Windows. I'm sure this executable is hidden, so it prevents many people from playing.

If you do find a solution to this, please post!

Good luck!

---

### Post by RC Howe on 2008-01-04
Warcraft has worked perfectly in versions of wine since around 0.9.36, I think. You just need to set the CD manually. Look under Drives and press the Autodetect button. If that doesn't work, try setting D: or another letter if D: is already in use (not C: ) to /media/cdrom0.

---

### Post by jordank on 2008-01-04
awesome i'll give that a try when i'm home. thanks!

---

### Post by jordank on 2008-01-04
Okay, well that was definitely one of the problems.  I clicked the autodetect button, and now I have a D: drive that reads the Cd rom.  That works, and I can now attempt to launch warcraft.

When I doubleclick the icon to launch it, my screen goes through a couple of phases.  First it goes black, then it goes white, then it goes very staticy in some parts and i can see part of my desktop, except it's in low resolution (like 400x600 or something).  From that step it doesn't move.

While still in the  low resolution mode i can force quit the program, but it continues to stay in the same resolution, but i can see my desktop and operate on my computer. 
I tried running the program again after seemingly force quiting the application but it tells me that warcraft is already running.

Couple of questions:

How do i manually change my resolution in ubuntu
What could be causing warcraft to not launch properly (Do I need to further configure wine?)

Thanks

---

### Post by jordank on 2008-01-04
Also, In wine do i need to configure my internet?  Like if I wanted to go online in a wine application (warcraft) do i have to somehow tell wine where my internet is located?

---

### Post by PmDematagoda on 2008-01-04
From what I experienced with Wine, you do not really need to configure Wine to have access to the internet, it should be working fine without any configuration.

---

### Post by jordank on 2008-01-04
Yeah i believe it's my version of wine that isn't working properly.
I made a new post asking how to use an older version of wine.

---

### Post by Thunar on 2008-01-04
> **jordank said:**
> I'm not seeing any labels tab?

Am I in the right place? And what do i do when I find this labels tab?

Check the screenshot.

The problem may be easier to solve than it seems. I noticed in the screenshot you provided of winecfg  that your "Windows Version" is set to "Windows 2000". Set it to "Windows XP" instead and see what happens. Worked for me when I had a similar problem. 

Also, for full-screen games it's sometimes nicer to have the "Allow the window manager to control the windows" box in the "Graphics" tab un-checked.

Good luck! :)

---

### Post by jordank on 2008-01-04
Alright well I did everything you said, and the program runs.  However, upon opening warcraft, i get an in-game error telling me that it couldn't make a sound base (sound isn't working)  also, when i try to connect to Battle.net (online play) it doesn't connect.
I read a couple other threads, and they said what i was thinking - that this version doesn't support battle.net, and i need to use an older version (0.9.43) if i want to use battlenet.

If i have the most recent version of wine, how can i downgrade to 0.9.43?
do i need to uninstall to do this?
If so, i already tried uninstalling, but it doens't seem to actually uninstall, because when i try to run the .deb package for 0.9.43 it tells me i already have that version installed.

What should my approach be?
And how do i get sound working?

---

### Post by Thunar on 2008-01-04
If you go back into winecfg (the screenshot you provided earlier) there's an "audio" tab where you must select an audio driver for audio to work in your games. The "OSS" driver seems to work best in Wine.

As for Battle Net, I wasn't aware that the newer version of Wine doesn't support it while the older one does... seems odd.

You can open up Synaptic Package Manager in the "System/Administraion" menu, search for Wine, then mark wine for "complete removal". Make sure you uninstall wine-dev as well.

Now you should be able to install an older version.

good luck! :)

---

### Post by jordank on 2008-01-04
I tried using OSS, nothing.

And the complete removal will remove everything about wine?

Including the .wine folder in my home directory, all the applications i've installed with wine, and remove the "wine" menu from my applications dropdown menu?

---

### Post by Thunar on 2008-01-04
I'm not sure if it will leave the directory intact, but it probably will as programs usually leave their directories behind. However, you will still need to reinstall all of your Wine applications after you reinstall wine. 

Your Wine directory is hidden in your "Home' folder, if you need to back something up it's in:

~/.wine/

or

/home/(Your Username)/.wine

As i said before, you might want to check out [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if your game is there and if it is maintained by someone. If it is, you can ask them for help as well, or read the existing documentation.

hope this helps!

:)

---

