---
title: "Adobe Flash Player installed but still doesn't work?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by 4iko on 2007-12-14
OK.I downloaded & installed AFP,restarted Firefox & PC but when I visit the website AFP doesn't work ...so I click on install missing plug-ins again and the following message comes across my screen:
 "Package 'flashplugin-nonfree' is already installed'
ANy idea what's wrong and how can I fix it?
 Thanks!

---

### Post by 4iko on 2007-12-15
I figured it out.I'll download it manually from the website but where should I save the file?
What's the Ubuntu's equivalent of Program Files?
 Thanks!

---

### Post by autocrosser on 2007-12-15
First--how did you install Flash Player? (Synaptic, Add/Remove, ?)
If you installed with one of the installer tools, you would have been asked if you wanted to enable the plug-in for your browser.

You are doing it the hard way if you downloaded it to install it.

Open Add/Remove & enable the "extra" repositories--then ask for "Ubuntu-restricted-extras"

---

### Post by Ribar on 2007-12-15
Here is the fix, fallow this and it will fix the problem. I did this last night and it works 100%

> Here is the 100% WORKING fix for youtube on Firefox.

I just installed a fresh ground-zero Ubuntu and I installed it, everything works 100%.

Visit this site:

[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)

Download the first option (.tar.gz)


After that finishes right click on the tar file and select "extract here". That's like unzipping in Windows.

Then open the folder and double click on the file "flashplayer-installer". Not the text one. And a pop-up should appear. Select "run in terminal" and then follow the instructions given.

Pretty simple to follow.


REMEMBER TO CLOSE ANY AND ALL FIREFOX WINDOWS BEFORE INSTALLING THIS THING OR IT WON'T WORK. Let me know how it goes.

---

### Post by autocrosser on 2007-12-15
If you ask for the restricted-extras, you will get much more than just flash-player---MS fonts, MP3 codecs, etc---recommended.

After that, you can change what you want.....just install thru the installer first to create a good upgrade path.

EDIT: look for the other post about Flash---updated info....

---

### Post by 4iko on 2007-12-15
OK.Problem solved.
 That's actually my 2nd time installing Ubuntu.The first time I installed it with a pirated version of XP ...I don't know if it has anything to do with that but nothing worked..but I remember I installed the AFP without any problems the first time...so I though it would be the same this time...
 what I did was ..there was one more plugin I needed to install when I clicked on "click here to download missing plugins"...I didn't need it the first time..but I installed it now and everything works fine!
 Anyway thanks for your help guys!
Take care!

---

### Post by RomeReactor on 2007-12-15
Hi. Did you install Gnash when Firefox showed you the plugins dialog? note that gnash is an open source implementation of Flash and, while it is very good, it still has a ways to go before it implements all the features of Adobe's proprietary Flash. The flashplugin-nonfree package has a bug where the system reports it is installed, but Firefox says it's not (see [this thread]("http://ubuntuforums.org/showthread.php?t=636397")).

You might want to keep Gnash, since it works well on most sites (including YouTube), while the fix becomes available in the repositories, or use the package posted in that thread.

---

### Post by 4iko on 2007-12-15
Yes,I did install Gnash.It turned out that's the only plugin I needed 4 the website I visited...but it didn't work on youtube at all so I had to install Adobe Flash Player too...
 Thanks again for your help guys!

---

### Post by mor gaiscioch on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See this thread for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

If you're running 32-bit Gutsy Gibbon, I suggest that you do the following in Terminal:

```
sudo apt-get remove --purge flashplugin-nonfree
```

and then simply download [this]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb") file.

---

