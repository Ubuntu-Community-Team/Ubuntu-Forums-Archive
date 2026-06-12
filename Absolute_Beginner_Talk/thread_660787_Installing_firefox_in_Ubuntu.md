---
title: "Installing firefox in Ubuntu?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by abk123 on 2008-01-07
Hello!!
I have downloaded **firefox-2.0.0.11.tar.gz**
Now i dont know how to install 
please help.......
Thank you.

---

### Post by mister_pink on 2008-01-07
That's the version that I have with ubuntu by default without doing anything. Any particular reason you want to install from that? It seems though that if for some reason you do want to manually install then that file is an archive that needs to be extracted. Are you sure that you don't already have it installed though? If not, then it would be far easier to select it in the Add/Remove tool.

---

### Post by Sef on 2008-01-07
Ubuntu upgraded to FireFox 2.0.0.11.  I just had to click update to get it.   Why are you doing it through a tar.gz method?

---

### Post by philinux on 2008-01-07
> **abk123 said:**
> Hello!!
I have downloaded **firefox-2.0.0.11.tar.gz**
Now i dont know how to install 
please help.......
Thank you.


Look under Applications>Internet>firefox

It's installed by default

---

### Post by AndyCooll on 2008-01-07
> **philinux said:**
> Look under Applications>Internet>firefox

It's installed by default

In fact if you're using the default Ubuntu it should be on the top taskbar as well.

:cool:

---

### Post by Lexyboy on 2008-01-07
I'm guessing they have an old version of ubuntu, must have downloaded it somehow...

If you extract the file (right click, extract) there should be a readme which will outline how to install it.

---

### Post by esva on 2008-01-09
I would like to know how to install it too... my family wants the browser in spanish

---

### Post by mister_pink on 2008-01-09
If you have it installed already you don't need to reinstall to change language. Go here: [http://support.mozilla.com/kb/Changing+the+language+pack](http://support.mozilla.com/kb/Changing+the+language+pack)

Edit: I imagine you want this: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/xpi/es-ES.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/xpi/es-ES.xpi) for spanish spanish or [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/xpi/es-AR.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/xpi/es-AR.xpi) for Argentinian etc spanish. Just click the links and it should work!

Edit 2: Copy and paste the addresses to the address bar and it won't ask you to add ubuntuforums.org to your safe list - right click the correct one and click "Copy Link Location"

---

### Post by RomeReactor on 2008-01-09
Hi. You can install language packs for Firefox from Synaptic; search for **mozilla-firefox-locale-es-ar** (Español-Argentina) or **mozilla-firefox-locale-es-es** (Español-España). Or to to install either from the terminal:
```
sudo apt-get install mozilla-firefox-locale-es-ar
```
or:
```
sudo apt-get install mozilla-firefox-locale-es-es
```

---

### Post by JoeyHustle on 2008-01-09
quick question, if you dled the file wouldnt you of downloaded it by going into firefox to get to the site? im pretty new to using ubuntu so i didnt know if it was always preloaded.

---

### Post by miqie on 2008-01-09
I had a Ubuntu CD sent to me and it has Firefox 2.0.0.6. on it.  I wanted to upgrade to upgrade to 2.0.0.11. so I downloaded it just like in Windows.  But I too don't know how to install it.  From now on, how do I upgrade this version?  I looked in Add/Remove, but didn't see an option to upgrade.  Could someone walk me through getting the latest version?  I guess the one I downloaded is headed for the trashcan.

---

### Post by flick on 2008-01-09
Which version of Ubuntu are you running? If it's the latest stable release, which is 7.10 or "Gutsy Gibbon", when you connect to the Internet you should see an Update Notification Icon appear in the upper panel of your desktop -- the icon looks sort of like an orange star. Click that and follow the prompts, that should get you updated to the newest Firefox.

OR, if you don't mind using the command line :

sudo apt-get update && sudo apt-get upgrade


If you're using an older version of Ubuntu, other procedures might be called for. Let us know.

---

### Post by RomeReactor on 2008-01-09
Hi miqie. Go to 'System->Adminsitration->Synaptic', there go to 'Settings->Repositories', and on the first tab (Ubuntu Software) make sure the first four boxes are checked. Close that window and, still in Synaptic, press the blue 'Reload' button. Now search for "Firefox", or close Synaptic and wait until the Update Manager starts to work and notifies you of the upgrades.

---

### Post by JoeyHustle on 2008-01-09
when you went to add/remove did you type in firefox. if not you should type it in and it should pop up then you check it and hit apply changes and it should pop up the firefox installation guide or just upgrade. also on the left of your where the time displays if there is an orange circle double click it. hoped that helped.

---

