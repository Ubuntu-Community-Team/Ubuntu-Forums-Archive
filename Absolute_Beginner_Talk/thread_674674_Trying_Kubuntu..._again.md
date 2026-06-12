---
title: "Trying Kubuntu... again"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by alquimista on 2008-01-21
Hello,

3 years ago I tried to get free of Windows XP on my Toshiba Satellite A60. I succeeded on having it 6 months, but unfortunately, among other problems, I had to develop a project that required full MS Office functionality, and back then, I did not find stable software that emulated office on Kubuntu (not even commercial software), so mainly because of this, I switched to WinXp (sadly).

Now, 3 years later, with the same hardware (60GB HD, 730 MB RAM) I prepared a 30 MB partition for Kubuntu 7.10. I was happy to see several improvements in the installation process. On my first try (2005), honestly I had to do a bunch of things on the console and "vi" to have things more or less running. Now I'm happy to see that calls to the console are much less necessary. I really fell well to come back and I hope to stay longer with Kubuntu; I just like KDE and Ubuntu as distro. Yet, I wanted to share with you some problems I still have in my present experience; as I said, less than 3 years ago, but still  a few;  I want to ask your help on the following points, for which some of them I have googled and searched on this forum, and for others, honestly, I have not... and I didn't want to open a different thread for each one of them, so please forgive me if I repeat problems already posted; be patience with this man that wants to be happy with Kubuntu again:

1- On the booth process, the screen is completely black; no process indicator not even those ASCII lists eith messages that Linux usually shows when loading itself. The Installation CD showed a nice splash screen indicating load process. Not after I installed it.

2- For booth, it takes 2:52 long minutes to show the login screen; and then, load the rest of KDE: total, 3:20 minutes.... that is to long for me... WinXP would take no more than 1:15 mins or so to load.

3- Yesterday I finally got Firefox to play videos in the Spanish BBC site (that I daily review) (one of the times I had to go to the console under root to move some plug ins from the mozilla directory, to the firefox directory). And for some wired reason, today the video on the same web site, just don't work. On the video area, it appears the banner of MPLayer, it indicates loading... and then it shows "stopped"; I try again, and nothing. I just now had to reboot the system because when I tried several times, all the system crashed: the hard disk kept running and everything went too slow, as if the memory was being exhausted.
I don have problems with flash based videos like in YouTube.

4- DVD movies does not work: I load a DVD with data, and even avi videos and have no problem with that. But when I load a DVD with and actual DVD movie format, does not work. I have seen several posts with this problem; I still have to try some of the solutions suggested. KPlayer shows  the black windows with no message at all. Kaffeine shows 2 errors (translated from spanish):
- Xine Error: no complement has been found to handle this resource: dvd:///dev/scd0
- Xine Error: source can not be read: you may not have access permissions to read the source.

I have tried several DVDs, that are normally read in WinXP or a DVD player. One thing I noticed is that the small green arrow head at the bottom right of the device icon, does not appear; I think that indicates is not mounted correctly? yet I have normal  access to tje DVD files contents, and when I want to play one of the VOB files...a couple of windows seem to flash... and then nothing happens.

5- For aMule, when I tried to get the list of available servers, the program crashed.

Well... so far these have been my problems, after 3 days of playing with Kubuntu. Even with those, so far I have not needed to boot the WinXP partition... (for home use).

I appreciate very much your help in advance; I like to recommend Kubuntu to many people that does not even know of the existence of Linux... Congratulations to Canonical, to the Ubuntu/Kubuntu community around the World for this effort :)

Guillermo

---

### Post by ddrplayer512 on 2008-01-22
I think that if you edit your /boot/grub/menu.lst and remove the splash argument for the kernel, you will get the ASCII text, maybe. I don't know.

For the DVD, go to videolan.org and follow the instructions to use their VLC Media Player, with DVD support.

That's all I know, hope that helped... :)

---

### Post by ddrplayer512 on 2008-01-22
You need a special library to play DVDs. That's why.

---

### Post by ugm6hr on 2008-01-22
Please note I use Gnome Ubuntu, so I hope these responses still aply to you (but I can't confirm):

1 & 2. See this: [http://ubuntuforums.org/showthread.php?p=3568252#post3568252](http://ubuntuforums.org/showthread.php?p=3568252#post3568252)

Seems 7.10 detects unusual resolution settings on laptops, which need to be manually adjusted.

3. BBC use Realplayer or WMP formats, neither of which plays nicely with Linux.  This works with WMP though:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Realplayer is a bit trickier (for me), since the Firefox plugin doesn't behave properly.  You can use MediaPlayerConnectivity Firefox plugin to make that work if you prefer.

4. See link in 3 for VLC.

5. Is aMule a torrent engine?  If so - try Ktorrent instead.

---

### Post by Hallvor on 2008-01-22
> **alquimista said:**
> 

5- For aMule, when I tried to get the list of available servers, the program crashed.



It is a bug. Just add a few servers manually from gruk or peerates, and you`ll be fine.

---

### Post by alquimista on 2008-01-28
Hi,
- I already applied a workarround the aMule bug with your suggestion
- link [http://ubuntuforums.org/showthread.p...52#post3568252](http://ubuntuforums.org/showthread.p...52#post3568252) helped to solve the boot problem; now the splash screen appears and Kubuntu loads much faster than winXP.
- I still have to work on BBC videos in Firefox, and have the DVD player working...


Thank you very much for your replies :)

Guillermo

---

