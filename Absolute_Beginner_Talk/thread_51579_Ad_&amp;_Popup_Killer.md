---
title: "Ad &amp; Popup Killer?"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-07-24
[Since my quest for temp/voltage monitoring turned out to be a complete bust, let's see if this will be any easier...]

Since switching to Linux, I sure miss the more effective ad & popup killers I had on my XP system.  FireFox seems to get some, but nowhere near enough.  Those flashing ads on pages are just driving me crazy.

Suggestions?

Thanks!

---

### Post by brathna on 2005-07-24
Have you tried the [Adblock](http://adblock.mozdev.org/) extension?

There's also a pre-built filterset [here](http://www.pierceive.com/filtersetg/) 

I never see an ad or popup ever.

---

### Post by aysiu on 2005-07-24
Try the Flashblock extension. The new tricky way to do pop-up ads is through Flash, not Javascript. Though, you can also use the No-Script extension, if you think it's Javascript that's causing the problem.

---

### Post by polo_step on 2005-07-24
[QUOTE=brathna]Have you tried the [Adblock](http://adblock.mozdev.org/) extension?

There's also a pre-built filterset [here](http://www.pierceive.com/filtersetg/) [/QUOTE]
How do you add these in Ubuntu/FireFox?

---

### Post by UbuWu on 2005-07-24
[QUOTE=polo_step]How do you add these in Ubuntu/FireFox?[/QUOTE]

Adblock:

Go to [https://addons.mozilla.org/extensions/](https://addons.mozilla.org/extensions/)
Click on adblock
Click on install now

---

### Post by polo_step on 2005-07-24
[QUOTE=UbuWu]Adblock:

Go to [https://addons.mozilla.org/extensions/](https://addons.mozilla.org/extensions/)
Click on adblock
Click on install now[/QUOTE]
Can't do it.  It shows that FireFox has to be upgraded before you can access that page.

Is there a Ubuntu Firefox that's compatible?  Here's what I have currently:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050524 Firefox/1.0 (Ubuntu package 1.0.2 MFSA2005-44)

---

### Post by bored2k on 2005-07-24
[QUOTE=polo_step]Can't do it.  It shows that FireFox has to be upgraded before you can access that page.

Is there a Ubuntu Firefox that's compatible?  Here's what I have currently:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050524 Firefox/1.0 (Ubuntu package 1.0.2 MFSA2005-44)[/QUOTE]
 In the location bar type about:config
Search for vendorsub, and change the value of general.useragent.vendorSub to 1.0.4 or higher (like 1.0.6) so you would be allowed to install extensions ;).

---

### Post by poofyhairguy on 2005-07-25
You have to click allow at the top to allow it to install. I vote for flashblock.....it does the job.

---

### Post by bored2k on 2005-07-25
[QUOTE=poofyhairguy]You have to click allow at the top to allow it to install. I vote for flashblock.....it does the job.[/QUOTE]
 I got so tired of Flash I ended up deleting the Flash software..

---

### Post by polo_step on 2005-07-25
Whoa!

Looks like I got that accomplished, though there were a couple of other small steps I had to do.

Man, lots less popups and banners!

Thanks to everyong who helped; it's nice to win one from time to time! :)

---

### Post by UbuWu on 2005-07-26
For other people reading this: you don't have to change the version number in firefox anymore, as when you have installed all the updates, you now have the latest (1.06) version of firefox, which will work fine!

---

