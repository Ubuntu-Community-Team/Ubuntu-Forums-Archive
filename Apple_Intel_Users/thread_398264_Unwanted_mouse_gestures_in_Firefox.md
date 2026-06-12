---
title: "Unwanted mouse gestures in Firefox"
date: 2007-03-31
forum: Apple Intel Users
---

### Post by PictureThis on 2007-03-31
It took me some time to figure out what was going on since I'm also still experiencing a somewhat jumpy and stuttering trackpad but this is what happens: whenever I perform a (non-intentionally) two-finger side scroll left/right Firefox (v2.0.0.3) will go back/forward one page in the current tab (equivalent commands are <alt><left arrow>/<alt><right arrow>). Extremely little movement is necessary to initiate the command and therefore interferes with my VertTwoFingerScroll. 

I didn't install a mouse gesture extension nor can I remember enabling mouse/trackpad gestures somewhere in Kubuntu. Anyone?

---

### Post by scorpio2002 on 2007-04-01
I'm experiencing the same problem...

---

### Post by Azathoth_ on 2007-04-01
I have the same problem in Feisty beta in i don't now why

---

### Post by PictureThis on 2007-04-01
It's pretty hard to master this flunky trackpad-version of the Minority Report UI (without the gloves)

---

### Post by Chrisj303 on 2007-04-03
> **PictureThis said:**
> It's pretty hard to master this flunky trackpad-version of the Minority Report UI (without the gloves)

:-D

---

### Post by PictureThis on 2007-04-10
Allright then, let's make some adjustments. I found the solution by coincidence on  [Alex S. Blog](http://strabes.wordpress.com/) who states:

> I have seen many forum posts about this problem 

I wonder whether he has read this one.. ):P 

Later I found the solution just about everywhere sigh.. Here's an almost three years old quote (can't find the right smiley here...) from [macosxhints](http://www.macosxhints.com/article.php?story=20040617000005758%3Cbr%20/%3E)

> The latest versions of Camino (0.8b) and Firefox (0.9) both use the horizontal scroll wheel to move back and forward in your history. This can be very annoying when using uControl for trackpad scrolling, but fortunately, with a bit of hacking, the old behavior (using horizontal scroll to scroll horizontally) can be restored. In Firefox, type about:config into the address bar and hit return. This gives you a list of all possible configuration options. The ones we want are those that start with mousewheel.horizscroll.withnokey. Make the following changes by double-clicking the appropriate option in the list:

mousewheel.horizscroll.withnokey.action => 0
mousewheel.horizscroll.withnokey.sysnumlines => true


On my quest I also found an elaborate explanation of the "about:config" settings, have a look at the [About:config entries](http://kb.mozillazine.org/About:config_entries) page.

[SIZE="1"]Edit: It seems something goes wrong when clicking the "About:config entries" link. The Firefox status bar will show "http://kb.mozillazine.org/About<b></b>:config_entries" and by clicking the link you'll reach mozillaZine page saying: "The requested page title was invalid". My hyperlink reads/should send you to "http://kb.mozillazine.org/About:config_entries". Just use the old copy/paste as a temporary(?) workaround...[/SIZE]

---

### Post by cyberdork33 on 2007-04-10
I was wondering why firefox kept jumping back every once in a while! I will have to try this later.

---

