---
title: "Newbie to Newbie: Getting things to work"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Ambimom on 2006-08-02
I installed Ubuntu two days ago and I love it. I can't believe how easy it was.  It's almost perfect but.....](*,) 

I installed Wine via  Synaptic Package Manager--at least it says it is installed-- I kept on searching for the application to launch it.  Eventually I noticed it on a command menu.  Someone should add a line or two in the properties to let us "newbies" in on the secret.  Regardless, I still don't know if it works or not.

Elsewhere, I read that MIRC could be used with Wine, but when I clicked on the "install with Wine" on the command menu, it didn't launch. I will probably use Opera Browser for IRC, which brings me to...

GAIM in which Yahoo Messenger just doesn't work and MSN Messenger was clutzy. Instead, I will use web-based Meebo and TheSwitchboard.CA, which always work and are very elegantly executed, especially in Firefox. No software installation needed.  

Switchboard requires  the Java Runtime plugin.  After trial and error I did find it hiding in the Synaptic Package Manager and installed it.  It was not easy to find.  There were several Java possibilities, but I did find the one that worked.

As for the Linux version of Skype...uh-uh. :(  Not good.   I can call computer-to-computer with no hassle, but I can't use Skypeout on Linux, nor video either. The Windows version is just plain better.

As for torrents and Usenet binaries, I'm sticking with Windows because I just have more space on my Windows drive, though it would be nice if someone would come up with Linux equivalents for Grabit and Utorrent.

All in all, Ubuntu is fantastic!  I am sure it will only get better.\\:D/

---

### Post by ironfistchamp on 2006-08-02
Ubuntu does rock doesn't it. I don't really understand your problem with wine. To use it get your .exe setup file and type  fom the command line wine <NAME OF FILE>. Make sure you are in the directory with the file in. 

I can't stand gaim so I use aMSN. A great thing you could use is Automatix. This can even setup aMSN. It isn't the latest version. If you wanted the latest version there are guides around the forums or you could post back on here and I can show you how I got mine.

[www.getautomatix.com](www.getautomatix.com)

This is a life saver it has tonnes of useful stuff to install. Very painless.

Skype is beyond me nothing I can suggest will help.

Automatix also has a couple of Bittorrent GUIs I think. Azures and Bit Tornado. They aren't as good as uTorrent (imho) but still pretty good.

Hope something in here was useful to you.

Ironfistchamp

---

### Post by nalmeth on 2006-08-02
First, I would recommend you pick up automatix. It will solve almost all of your issues right now.

Wine is a windows compatibility layer, not a program. 
First, hit ALT-F2, and run winecfg to create the wine directories.
Right-click your .exe and hit "run with wine" to use it. Or go into properties and set wine to run all .exes by default, and double-click the .exe in the future.

XCHAT is a great equivalent for Mirc, though mIRC is supposed to run in wine.

I use amsn for msn messenging, it does video conferencing. To get the latest use automatix.

I agree with you with skype, the windows version is plain better. But don't blame linux for that, blame skype. 

There are MANY linux torrent apps, and I've found them much better than windows counter-parts, though it's been some time since I've used windows for anything.

Azureus and ktorrent come to mind. Ktorrent doing the same things as azureus, but with lighter footprint and no java.

Have fun with Ubuntu, glad to see you making it work!

---

### Post by ironfistchamp on 2006-08-02
I thougght automatix only had 0.95 for amsn. The rc1 for 0.96 is out and a beta for 0.97. Or is my automatix out of date?

---

### Post by Ambimom on 2006-08-03
Thanks everyone... 

I'm sort of clueless about how to use automatix..... it says

 *"just add the appropriate entry to your /etc/apt/sources.list with your text editor of choice"*

huh?  How would I do that?

As for wine, I will try Alt F2, but when? When I'm trying to open a Windows application?  

I did try that aMSN program, but my webcam did not work in it.  I have Logitech Quickcam Pro 4000.  

As for IRC, I've tested the chat in Opera Browser which works! 

I think Ubuntu is terrific!  And thank you all!

---

### Post by ironfistchamp on 2006-08-03
To edit the sources list type

```

sudo gedit /etc/apt/sources.list

```

Then add in the lines it says. Be careful when editing this file. Might be a good idea to make a backup of it by typing 

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```

For wine, when you want to install your progam you get the .exe, open the terminal, change into the directory and type wine <filename> OR right click on the file you want and say open with Wine. This will run the windows installer. It should create a shortcut on the desktop.

---

