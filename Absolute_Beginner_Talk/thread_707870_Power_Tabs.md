---
title: "Power Tabs?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-25
I'm trying to download some song tabs. and it's telling me i need power tabs or something?
i don't know what it's talking about...i'm just learning guitar.
haha

---

### Post by SOULRiDER on 2008-02-25
Could you please elaborate?  Where are you downloading them from? What is telling you you need power tabs?

More info is needed for us to be able to help you!

---

### Post by speeddemon8803 on 2008-02-25
You want Guitar Pro for linux correct? if so go to terminal and type in > sudo aptitude install dguitar  If its TablEdit that you wish to get instead type in >  sudo aptitude install songwrite

Hope this helps.

---

### Post by angry_johnnie on 2008-02-26
Found a couple:

1.  Tux Guitar.

I know it opens Guitar Pro files (don't know for sure about powertab --which i've never used).  But, according to this thread, it does.

[http://ubuntuforums.org/showthread.php?t=357592](http://ubuntuforums.org/showthread.php?t=357592)

Here's the link for tux guitar (with a fairly easy to follow installation guide)

[http://www.tuxguitar.com.ar/tgwiki/doku.php?id=doc:install_ubuntu](http://www.tuxguitar.com.ar/tgwiki/doku.php?id=doc:install_ubuntu)

You may also need to install timidity in order for this to work.

```
sudo apt-get install timidity
```

2.  The other option would be to download the powertab editor from this location (softpedia)

[http://www.softpedia.com/get/Authoring-tools/Authoring-Related/Power-Tab-Editor.shtml](http://www.softpedia.com/get/Authoring-tools/Authoring-Related/Power-Tab-Editor.shtml)

it's a zip file.  so unzip it first.  Create a new folder and paste it there.  Then right click on it and choose extract here.  THEN you'll have a windows executable, called setup.exe

So you would have to install wine first.
open a terminal and type

```
sudo apt-get install wine
```

then

Navigate to where setup.exe ist and open a terminal there.  Or open a terminal anywhere and type cd /path/to/file

then type

```
wine setup.exe
```

Then it will install it in your machine, just as if you were running Windows.
But, then again, if you ask me, I'd say go for tux guitar.
Things tend to get messy with wine, especially the fonts.  I installed guitar pro 5 once, and the only way I could actually read anything was to copy all the fonts from a working windows installation and paste them into wine's font directory.  There may be another workaround for this, but this is just what I did.

I found another one called Kguitar, but I'm not sure whether it'll play powertabs.  Same goes for Gnometab.  They should both be in your repositories, in case you decide to try them out.

---

### Post by sayakb on 2008-02-26
> **RadiationHazard said:**
> I'm trying to download some song tabs. and it's telling me i need power tabs or something?
i don't know what it's talking about...i'm just learning guitar.
haha

[http://en.wikipedia.org/wiki/Guitar_chord](http://en.wikipedia.org/wiki/Guitar_chord)
:D :D :D

Anyway, PowerTabs is a win32 app as I remember...

---

### Post by PinkFloyd102489 on 2008-02-26
Powertab is a Windows based MIDI guitar tab player, I have it on my computer. You'll have to run it under WINE if you absolutely want it, because I dont think that any other program plays the ptb files.

---

### Post by infomissing123 on 2008-03-07
I've been dealing with this problem for a while now.  There are 3 ways to tackle it:
1).  Install Windows on a virtual machine and install powertab within.  So far, I've tried VMware and Parallels.  This works but there are some latency issues in VMware.  Sounds skips and jumps around a little bit.  Adding ram helped but the problem still remains on really busy tab files.  I'm not sure why but Parallels seems to smoke VMware when it comes to MIDI playback.  Flawless playback.

2).  Newest version of TuxGuitar plays and edits ptb files.  It's not perfect.  Some repeats do not read in correctly, and sometimes 2 parallel guitar tracks will get out of sync but it's usable.  I don't remember off the top of my head if it allows you to save them in ptb format.  I wouldn't trust this feature.  Apparently, the format of ptb files is really wacky.

3).  Install wine and run powertab and the newest version of guitar pro (v5.2 at the moment of this writing).  This is my preferred way of doing it.  Wine 0.9.46 seems to install both fine.  Guitar pro plays files back (and it can read ptb files).  Powertab opens and can edit but won't play.  This drives me nuts still since I used to have this working and I know it's not a midi issue since Guitar pro uses the same damn method.  Anyway, you can edit with powertab and use guitar pro to play back.  That's what I'm doing.  

If anyone has any insight, feel free to share.

---

