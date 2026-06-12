---
title: "TurboTax/and adobe"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-04-15
I did my taxes with turbo tax and all went well. However in order to view past returns in their vault, I get a messagage that says I need Adobe Reader. Well I allready have adobe reader. I note this in other things as well for instance I might get a msg when trying to watch a online video, you need micromedia flash player, which I already have as well. I would like to clear this up, but how? Using edgy 6.10
:D

---

### Post by Famicommie on 2007-04-15
Having Adobe Reader and Flashplayer installed is fine and good, but what it specifcally wants are the Firefox plugins for Adobe Reader and Adobe Flashplayer.

In a terminal, run:
```
sudo aptitude install libflash-mozplugin mozilla-acroread
```

---

### Post by rosswmcgee on 2007-04-15
I certainly never run out of things to learn. OK did now I will see how it works/and thank you.

---

### Post by rosswmcgee on 2007-04-15
What are my system docs?  I did run turbo again and it still asks for adobe reader.

---

### Post by Famicommie on 2007-04-16
Heh, that "system docs" line is just my signature. It wasn't directed at you personally. The system docs *are* useful, though. You can find them by going to System->Help->System Documentation.

After you ran aptitude, did you close firefox? Firefox plugins require firefox to be restarted before they take effect.

If that doesn't work, try installing the plugins through [Automatix](http://www.getautomatix.com). I used Automatix, and I have no problem with .pdf files or using flash.

---

### Post by lamalex on 2007-04-16
how are you running turbotax? is it now working under wine? fully functional?

---

### Post by rosswmcgee on 2007-04-16
I have always used Firefox for Turbo Tax. I just ignore the warning that says you do not have the right browser and press continue, then log on and every thing works just fine. I saw the wine thing, I do not even know what wine is. What is it?

---

### Post by rosswmcgee on 2007-04-16
I have no problem with PDF files either it just the Turbotax thing, they say I do not have Adobe.

---

### Post by Famicommie on 2007-04-16
WINE is a program allowing you to run Windows programs in Linux. I think that lamalex is under the assumption tha tyou used the TurboTax application to do your taxes, not the website. I also used the website to do my taxes.

Did restarting firefox fix your reader problem?

---

### Post by rosswmcgee on 2007-04-16
Every thing on Turbo Tax Online works fine but I can only get into the vault using Windows on my wifes machine. There are problems when we Linux folks operate outside the mainstream. Online video sites all vary,
CNN, Fox, Bloomberg CBS for instance. I can play CNN videos with some tweaking, Fox I get sound no video, Bloomberg I can get videos and sound some of the time, CBS can not do innertube. So the industry could use some standarization and Ubuntu needs to work on a way not to have to use VLC and a bunch of other apps.

---

