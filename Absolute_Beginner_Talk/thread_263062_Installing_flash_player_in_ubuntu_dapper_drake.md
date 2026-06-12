---
title: "Installing flash player in ubuntu dapper drake"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-09-22
i got my 50 dollar ebay computer in the mail yesterday and i am amazed how everything worked! Internet worked right away and no problems (except the sound card dont work). How can I install the flash plugin for firefox?

---

### Post by uruahv on 2006-09-22
I think the easiest way for a beginner would be to use Automatix ([http://www.getautomatix.org)]("http://www.automatix.org%29"). With this you could also install lots of other plugins and stuff you'll need the most.

---

### Post by aysiu on 2006-09-22
1. Enable extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Then paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

### Post by SunnyRabbiera on 2006-09-22
just remember the lastest flash (flahs 9) is not availible for linux so pages that need flash 9 will not work.
this is because the company that owns flash adobe hates linux...
the easiest way to get the latest flash is though crossover office, though it has a pracetag on it...

---

### Post by aysiu on 2006-09-22
Crossover Office? God, no! You can use Wine... or even just trick sites into thinking you're running Flash 9.

More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Metacarpal on 2006-09-22
> **SunnyRabbiera said:**
> just remember the lastest flash (flahs 9) is not availible for linux so pages that need flash 9 will not work.
this is because the company that owns flash adobe hates linux...
the easiest way to get the latest flash is though crossover office, though it has a pracetag on it...

Flash 9 is in development for Linux, they're just being a little slow about it.  They're nearly at beta testing, and the official release is slated for early 2007 (very late, IMO, but it's coming...) - [Keep up to date here]("http://blogs.adobe.com/penguin.swf/").

---

### Post by SunnyRabbiera on 2006-09-22
> **aysiu said:**
> Crossover Office? God, no! You can use Wine... or even just trick sites into thinking you're running Flash 9.

More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

well wine is not easy to work with, its more for the professional who knows what they are doing, wine takes some time to configure.
crossover does the same without as much hassle.

---

### Post by sdubois92 on 2006-09-22
thanks everyone, got automatix, now all i need is a new sound card.

---

### Post by aysiu on 2006-09-22
> **SunnyRabbiera said:**
> well wine is not easy to work with, its more for the professional who knows what they are doing, wine takes some time to configure.
crossover does the same without as much hassle.
Wine *can* take a bit of configuring, but if you just want to install Flash 9 with Windows Firefox using Wine, it's really quite simple.

See the link I posted earlier.

---

### Post by Linducker on 2006-09-22
Just click on the "Unknown plugin" in the browser if you are at a flash site and then click agree then install.

or


Downlaod the tar.gz file frome macromaedia.com, unpack it and run the install instructions(ther at macromedia)

Hope it works for you!

---

### Post by Drakkor on 2006-09-22
Ok,trying to install Firefox with wine... when I right-click the setup.exe file I get an error box that says: 7-Zip Cannot create temp folder archive. :mad:

---

### Post by SunnyRabbiera on 2006-09-22
> **aysiu said:**
> Wine *can* take a bit of configuring, but if you just want to install Flash 9 with Windows Firefox using Wine, it's really quite simple.

See the link I posted earlier.

I just find crossover more newb friendly, plus some of its money does go to the wine project.

---

### Post by aysiu on 2006-09-22
> **SunnyRabbiera said:**
> I just find crossover more newb friendly, plus some of its money does go to the wine project.
As I said before, Wine *can* take a lot of configuring, but it depends on the task.

The task of installing Windows Firefox in Wine and then getting Flash 9 from there is just about as "newb-friendly" as it gets, especially if you follow the tutorial in the link I posted earlier.

---

### Post by Drakkor on 2006-09-22
aysiu,did you see my error post above ? I am trying to follow the instructions in the link ! Thanks ;)

---

### Post by aysiu on 2006-09-22
> **Drakkor said:**
> Ok,trying to install Firefox with wine... when I right-click the setup.exe file I get an error box that says: 7-Zip Cannot create temp folder archive. :mad:
You've already installed Wine?

---

### Post by Drakkor on 2006-09-22
Yep,

---

### Post by BLTicklemonster on 2006-09-22
doesn't work for me either. I get a message that it can't install and to go get a different version, I do, and it says there's a dll file missing.

---

### Post by aysiu on 2006-09-22
I can't believe this is happening. Did something change? I think I made that tutorial only a week or two ago (i.e., not that long ago).

What happens, Drakkor, when you try launching it from the terminal? ```
cd ~/Desktop
wine "Firefox Setup 1.5.0.7.exe"
```

---

### Post by tuxcantfly on 2006-09-22
7-zip is associated with .exe files. change it to wine.

---

### Post by Drakkor on 2006-09-22
@  aysiu 
Yeah I thought I'd do sudo <file> thinking it was a permission problem but the same thing happens !

---

### Post by aysiu on 2006-09-22
tuxcantfly's suggestion...?

---

### Post by Drakkor on 2006-09-22
If you mean changing .exe to .wine , it doesn't work

---

### Post by BLTicklemonster on 2006-09-22
For what it's worth, regular flash plays fine, just the new stuff won't. Like the Al Yankovich video that just got leaked. I can't play it.

---

### Post by aysiu on 2006-09-22
> **Drakkor said:**
> If you mean changing .exe to .wine , it doesn't work
No, I think it's changing the file association. Right now, Ubuntu wants to open .exe files with 7-zip instead of with Wine.

Right-click on the .exe, go to **Properties** and **Open With** and then make sure the black circle is next to Wine instead of 7-Zip.

---

### Post by Drakkor on 2006-09-22
That would have sounded logical except when I do right-click the Firefox
setup.exe file I do get "Open with Wine Windows Emulator" , and the properties are set to open with wine. I just can't figure it out. I even
uninstalled and reinstalled wine , no go ! :(

---

### Post by aysiu on 2006-09-22
I'm not sure what 7-zip is, but it appears to be interfering with Wine somehow.

The weird thing is, [when I Google your error, **nothing** comes up...](http://www.google.com/search?hl=en&q=%22can+not+create+temp+folder+archive%22&btnG=Google+Search)

---

### Post by Drakkor on 2006-09-22
Ok,I copied the setup.exe file into .wine program files with gksudo,and got the install program in Spanish, I think,lol ! :p

---

### Post by Drakkor on 2006-09-22
Anyone know how to change the language from Spanish to English ?  I tried this but the link can't be displayed ! [http://www.ubuntuforums.org/showthread.php?t=212310](http://www.ubuntuforums.org/showthread.php?t=212310)
The menu is all in Spanish !

---

### Post by BLTicklemonster on 2006-09-22
7-zip is a file compression program like rar and winzip. I'd remove it using synaptic for a while til this is settled, or if you never use it, just fuggedaboudit

---

### Post by aysiu on 2006-09-22
Sounds as if you downloaded the wrong version...

Try this one:
[http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.7/linux-i686/en-US/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.7/linux-i686/en-US/)

---

