---
title: "Itunes???"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by philh123 on 2008-03-21
I'm very new to linux and ubuntu. I've Have worked with windows starting with 98 and ending with XPPro. My experience with computers goes back to the day when we were loading programs with pieces of cardboard that had holes punched in them on an 029.

Any way, I have recently installed UBUNTU and am really happy with the result. I have a lot of questions that I will be able to get assistance with through these forums

The posts regarding itunes seem to be dated. Is there anything new on the horizon? I saw in one of the posts a mention of an upgrade that might address this issue. Is this the upgrade that is suggested when I do updates? I saw in another of the posts a reference to "stripping out DRM?" If I could just listen to the music I would be appeased.

If this  (stripping out he DRM) is likely to work could someone please give me specifics. 
Thanx,

---

### Post by Doctor Debian on 2008-03-21
I recommend just using Amarok to manage your ipod. It can be installed by entering this command in terminal:

```
sudo apt-get install amarok
```

I don't know much about DRM, but Amarok should manage your music well. You could also use the included app called rhythmbox.

Doc Deb

---

### Post by stchman on 2008-03-21
> **philh123 said:**
> I'm very new to linux and ubuntu. I've Have worked with windows starting with 98 and ending with XPPro. My experience with computers goes back to the day when we were loading programs with pieces of cardboard that had holes punched in them on an 029.

Any way, I have recently installed UBUNTU and am really happy with the result. I have a lot of questions that I will be able to get assistance with through these forums

The posts regarding itunes seem to be dated. Is there anything new on the horizon? I saw in one of the posts a mention of an upgrade that might address this issue. Is this the upgrade that is suggested when I do updates? I saw in another of the posts a reference to "stripping out DRM?" If I could just listen to the music I would be appeased.

If this  (stripping out he DRM) is likely to work could someone please give me specifics. 
Thanx,

Ubuntu supports iPods OOB.  Rhythmbox is installed by default and it does iPod management.

---

### Post by SunnyRabbiera on 2008-03-21
Currently there is not an itunes for linux though some reported mixed success with installing itunes via WINE a way to install windows programs in linux though its win some loose some.
Now we have itunes alternatives, do you use itunes to listen to music or purchase it?
even if you do purchase music there are ways to buy music online, such as amazon and a few others.

---

### Post by Doctor Debian on 2008-03-21
Also, I believe Crossover Office works very well with iTunes if you need it for purchasing music.

Doc Deb

---

### Post by SunnyRabbiera on 2008-03-21
yes though it is not free.
I cannot vouch for itunes currently, you can try to install wine and install itunes in wine but if it will work is unknown.

---

### Post by jpdamigaman on 2008-03-21
HI I have an ipod touch and tried it in ubuntu when I plug it in it is recognised as a photo device.

I tried GTKPOD but it wouldn't recognise it at all.

still trying though to find a solution!

---

### Post by Steve Angelidis on 2008-03-22
From what I've read iTunes will not work with Wine or CrossOver Office. See Codewseavers website. (They produce and sell CrossOver Office and **_they_** say iTunes doesn't run.)

I have also read that some virtual machine emulators such as VirtualBox also don't run iTunes although I don't know about the others (Parallels, VMWare etc...).

If you want to run the actual iTunes, dual booting is probably your best bet.

If you want to use an ipod with Ubuntu, then get your music from an mp3 source such as Amazon or Puretracks and convert your existing Apple derived music to mp3. Then you can use Rhythmbox, Amarok, Exaile or other Linux music player/downloader. They will run your ipod just like iTunes but without Apple's proprietary formatted music.

All the best.

---

### Post by cisforcojo on 2008-03-22
jpdamigaman, I agree gtkpod is garbage. I suggest you check out the program, Floola.
[www.floola.com](www.floola.com)

As for the music player, I'm partial to Exaile. I used to be a big Amarok fan but I became weary of its instability (in GNOME) and it's bloatedness. It's too big for what it is.

---

### Post by Mulenmar on 2008-03-22
I don't understand -- RhythmBox says I need an MP3 and AAC plugin?
So how does converting everything to Mp3 help?

---

### Post by stchman on 2008-03-23
> **Mulenmar said:**
> I don't understand -- RhythmBox says I need an MP3 and AAC plugin?
So how does converting everything to Mp3 help?

You need the proprietary codecs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

---

### Post by 3rdalbum on 2008-03-23
Stripping out DRM can currently only be done on a real Windows system with iTunes, but it's a quick and painless operation! It results in unprotected AAC files that will play on your Linux system with the right codec.

I'm not sure what the Ubuntu Forums position on me posting a link would be, but you should find some links if you look up "Hymn project".

---

