---
title: "Software updates for Firefox"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Nigel Hewlett on 2007-03-04
I have been offered 4 new software updates for firefox, as follows:
firefox
New version: 1.5 dfsg+1.5.0.10.-0ubuntu0.6.06.2
firefox-gnome-support
New version: [as above]
libnspr4
New version: [as above]
libnss3
new version: [as above]

Whe I try to get details it tells me details cannot be found and to check my network connection (which is fine).  I am reluctant to download them because:
As far as I know I successfully updated to Firefox 2.0.0.1 a couple of weeks ago (when I click on Help, About Mozilla Firefox I get a screen that specifies "Firex 2.0.0.1"  I haven't been able to find any other info about which version I am running.)

Should I download these updates or not?  It looks as though, if I do so, I will revert to Firefox 1.5.

Nigel Hewlett

---

### Post by aysiu on 2007-03-04
How did you install Firefox 2.0.0.1?

My guess is that you installed it from Mozilla's website, either manually or through a script. If so, that installation is complete separate from the Ubuntu Firefox. In other words, you have two Firefoxes installed--2.0.0.1 from Mozilla and 1.5.0.10 from Ubuntu.

Updating the Ubuntu one will not change your Mozilla one to 1.5

---

### Post by Blutack on 2007-03-04
You are running dapper, which defaults to FF1.5.  When you updated I imagine you grabbed FF off the mozilla site and switched the binaries (the bit that makes it run).  Your system doesn't know this however and APT (synaptic) thinks that FF1.5 is still installed.  Your best solution is probably to try and uninstall FF1.5 - however, I would back up your data first just in case (its in your home folder in the .mozilla folder).  Hope this helps.

---

### Post by aysiu on 2007-03-04
> **Blutack said:**
> Your best solution is probably to try and uninstall FF1.5 Not according to [the Ubuntu Wiki](https://help.ubuntu.com/community/FirefoxNewVersion): [quote=Wiki on Firefox]Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine.[/quote]

---

### Post by Nigel Hewlett on 2007-03-04
Many thanks.  I updated to Firefox 2 using the guide at psychocats.net/ubuntu/firefox.  I downloaded the script linked there and pasted the command into the terminal.  It seemed to work fine and Firefox is working great.
It sounds like I should just go ahead and install the updates.
Nigel Hewlett

---

### Post by aysiu on 2007-03-04
> **Nigel Hewlett said:**
> Many thanks.  I updated to Firefox 2 using the guide at psychocats.net/ubuntu/firefox.  I downloaded the script linked there and pasted the command into the terminal.  It seemed to work fine and Firefox is working great.
It sounds like I should just go ahead and install the updates.
Nigel Hewlett
Couldn't hurt either way. If you want, you can also [lock the Ubuntu version of Firefox.](http://ubuntuforums.org/showthread.php?p=2076216#post2076216)

---

