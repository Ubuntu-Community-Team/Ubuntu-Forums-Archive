---
title: "yahoo music video site won't play video (screenshot included)"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2008-02-10
hey I went to the yahoo music video site and I got a message that my OS won't play the video's.  I then updated everything (flash included) and no i don't have compiz or beryl.  Does anyone else have a problem with this site or is it just me?  If you have a minute check it out before writing me back!  Thanks.

---

### Post by JoshuaRL on 2008-02-10
Well, I'm on a work XP PC right now so I can't check for you.  But that looks like they're blocking Linux.  I recently switched cable modems and it asked me to update them on what I had.  When I tried from Linux Mint it said that they didn't support my OS.  I hope that isn't the problem, but it looks like it.

Have you tried their help page linked there?  What does it say?

This is just the first step in the Microsoft takeover of Yahoo.:lolflag:

---

### Post by spiderbatdad on 2008-02-10
just watched Alicia keyes from top 100 list, no problem

---

### Post by spiderbatdad on 2008-02-10
have you installed ubuntu-restricted-extras?

---

### Post by badmedic on 2008-02-10
I just checked from my system, and am able to see videos so they aren't blocking Linux. 

You may need some added codecs or the latest Flash player to see the format they use... 

I have some extra stuff installed from the Medibuntu repository ([http://medibuntu.org/](http://medibuntu.org/)) . I also have the latest non-free flash player (Flash 9) installed from Adobe.

---

### Post by JoshuaRL on 2008-02-10
> **spiderbatdad said:**
> just watched Alicia keyes from top 100 list, no problem

Good, then you can disregard my advice.  That's, amazingly enough, great news.

---

### Post by spiderbatdad on 2008-02-10
the home page did alert me of a pop-up block and suggested i needed to change my browser settings...no doubt an attempt to plant some tracking software in firefox, but I navigated to videos using the tabs at the top of the page.

---

### Post by ed-koala on 2008-02-10
There have also been issues upgrading to the latest Flash Player.  Seems it doesn't actually update and will break your flash plugin. Try this to see if it might fix your problem:

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I had to do this myself after "upgrading".  It made my PC reboot on certain web pages until I fixed it.

---

### Post by spiderbatdad on 2008-02-10
> **ed-koala said:**
> There have also been issues upgrading to the latest Flash Player.  Seems it doesn't actually update and will break your flash plugin. Try this to see if it might fix your problem:

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I had to do this myself after "upgrading".  It made my PC reboot on certain web pages until I fixed it.


before doing an action like that, it is probably a good idea to```
sudo apt-get upgrade
sudo apt-get update
``` or one is likely to re-install the same unpatched package.

---

### Post by Shrek X on 2008-02-10
I had what sounds like the same issue with flash.... you might try this, worked for me, and make sure firefox is closed when you do it or it wont install the plugin.  


> **RomeReactor said:**
> Hi. This problem has been discussed many times, and it's directly related to [this bug]("http://ubuntuforums.org/showthread.php?t=636397"). To get Flash working, download one of the following packages:

* [flashplugin-nonfree for Ubuntu 7.10 32-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")
* [flashplugin-nonfree for Ubuntu 7.10 64-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466")

Close Firefox, and double-click the package to install. Make sure gnash is not installed:
```
sudo aptitude remove --purge gnash mozilla-plugin-gnash
```

---

### Post by JoshuaRL on 2008-02-11
> **Shrek X said:**
> I had what sounds like the same issue with flash.... you might try this, worked for me, and make sure firefox is closed when you do it or it wont install the plugin.

That's been fixed quite recently.  I would follow what spiderbatdad says.  Gnash is open source and a great idea, but I have had nothing but trouble with it.  I believe it is still in beta, and has stability issues.  Until they get the major bugs fixed I would suggest for the average user to just use flash.

Unless you're Richard Stallman  :lolflag:

---

