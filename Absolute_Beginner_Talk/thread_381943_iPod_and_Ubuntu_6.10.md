---
title: "iPod and Ubuntu 6.10"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by marsprincess on 2007-03-11
Hello, 
I have an iPod Shuffle I want to use with my computer that is running Edubuntu 6.10.  Is iTunes compatiblel with Linux or if not is there a program I can use in place of iTunes?

---

### Post by Crooksey on 2007-03-11
GTKPod

[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

---

### Post by marsprincess on 2007-03-11
Thank you I'll make sure I look into that.:KS

---

### Post by igknighted on 2007-03-11
Rhythmbox and Amarok can also sync with ipods.

---

### Post by marsprincess on 2007-03-11
I downloaded gtkpod and it is on my desktop.  How do I install it.  I see that it is a tar.gz file.  Thanks for the help.:)

---

### Post by igknighted on 2007-03-11
You don't ever want to go online and download programs (except as a last resort), almost everything is available in the repo's.  Open a terminal and type:
```
sudo aptitude install gtkpod
```
or open synaptic and install the package gtkpod

---

### Post by marsprincess on 2007-03-11
Got it, thanks.  Another question if you don't mind.  I had music on my iPod and it seems that gtkpod sees it.  If I was wanting to add more music to it, do I have to either burn it to  a CD then run on my edubuntu computer.  Or can I purchase music through gtkpod.  thanks for the help.:)

---

### Post by igknighted on 2007-03-11
You can purchase music on linux, but make sure there is no DRM on it.  If you *need* to use that wretched ITMS then you need to download/reimport (this will result in extra loss of audio quality).  An alternative might be to run iTunes in vmware if it is that impotrant.  Amarok has its own store (not that good), or just buy CDs (better audio quality... only one import).

---

### Post by marsprincess on 2007-03-11
I decided to burn it to CD and add it to gtkpod, but when I insert the disk, i get Sound Juicer Extractor,  How can I move the music on the CD to GTKPod.  thanks for the help igknighted you have been very helpful.:)

---

### Post by djlyx on 2007-03-12
Sound Juicer is a great program, however it natively rips CDs into a Free Open Source Format called "ogg Vorbis".  Unfortunately iPods do not play "ogg" files.  Go here to configure it to rip MP3s ( [http://www.emcken.dk/weblog/archives...nd-Juicer.html](http://www.emcken.dk/weblog/archives...nd-Juicer.html) )  Then after that, I think you can use AmaroK (a music player program similar to itunes) to copy songs into your iPod.  AmaroK too needs to be configured to work with your iPod, its pretty easy though.


If you haven't already done so, make sure you download (through synaptic) the gstreamer "ugly" drivers so that you have the ability to play restricted formats in Ubuntu.

Hope this helps.

---

### Post by dustigroove on 2007-03-12
[Songbird]("http://www.songbirdnest.com/") with the iPod Device Support add-on is a great option. While the player is still in it's infancy, it is quite fully featured and fairly stable.

**Additional Resources**:
[http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)
(Please note - the latest version differs from the one provided in the guide.)

---

