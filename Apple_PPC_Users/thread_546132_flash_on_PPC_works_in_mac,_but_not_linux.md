---
title: "flash on PPC: works in mac, but not linux?"
date: 2007-09-08
forum: Apple PPC Users
---

### Post by wickstopher on 2007-09-08
Hi, there!  I just inherited a g4 powerbook, and got a dual boot install of OSX Panther/Kubuntu Feisty going (awesome!).  Now, this may seem like a stupid question, but from what I've read, the reason there is no flash in linux for PPC is that it's not supported by the processor architecture.  If that is in fact the case, why does flash work out of the box with Safari for me in OSX?  It seems to me that there must be a way of doing it in linux...

---

### Post by zekica on 2007-09-08
Mac OS X has different API and Adobe has not releases it's Linux version of flash player for PPC architecture (nor for amd64), so even if they released flash for OS X it is not the same version of their product (Flash Player).

This is one of the reasons closed source software is not good.

---

### Post by stmiller on 2007-09-08
Flash works fine on the Power architecture, it is just that Adobe has not released a version for PowerPC Linux. The Adobe Linux flash developer is very hostile towards any other architecture than x86, unfortunately. Despite tons of comments asking for x86_64 and PowerPC versions, he constantly dismisses those architectures for who knows what reason. You can read his blog [here]("http://blogs.adobe.com/penguin.swf/") with lots of user comments and feedback.

There is an open source alternative for [PowerPC Linux users: Gnash]("https://wiki.ubuntu.com/PowerPCFAQ#head-b7d7a28d512999b3729800b8cd1cb796300111d8"). 
Gnash as of ver. 0.8.0 is flash 7 equivalent and also plays youtube and other video here and there. So it's basically flash 7 + things from flash 9.

---

### Post by MisterRik on 2007-09-09
Hey **stmiller**, thanks for the link to Gnash. Following the instructions on that page, I managed to [apparently] get Gnash installed. It appears in the Applications -> Sound & Video menu, anyway.

However, when I select it from the menu, nothing seems to happen. Are there additional steps I need to take?

Also, it says this at the link you provided:

> Gnash 0.7.2 (default version included with Feisty) has support for most basic Flash webpages but not Flash video in the browser.

... but I'm not seeing any support at all for any kind of Flash. Clearly, I've missed something. Suggestions?

I'm using Firefox, for the record.

---

### Post by wimpytx on 2007-09-09
you downloaded the wrong gnash version its .08 or something like that . the old gnash is supposed to open in a window if u watch something that is in flash format. it wont open if u click on it. the new gnash supports watching flash in ur web browser so it wont open in a seperate windows just like normal flash. Ive never got it to work but it no longer says i need to install missing plugins.

---

### Post by MisterRik on 2007-09-09
According to the Add/Remove Applications utility, I have version 0.8.0 installed:

> Version: 0.8.0~cvs20070611.1016-1ubuntu3~feisty1 (gnash)

I still get the the "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player." when I visit YouTube, and no functioning Flash on any other site.

---

### Post by stmiller on 2007-09-09
In Firefox, type

```

about:plugins

```

in the address bar and hit enter. Make sure that says Gnash 0.8.0 there somewhere. If it doesn't, let us know.

Then if gnash 0.8.0 is installed ok, try a page like 

[http://www.cowonglobal.com/](http://www.cowonglobal.com/)

to see if it works. That page DOES work for me, using Gnash 0.8.1 that I compiled. Including the nav bar at the top, and flash movies playing on the side.

Gnash does take a good CPU to play back flash movies, such as youtube. So if you have a very old machine, it will probably have some problems. You will probably need at least a 400Mhz PowerPC cpu, at the very least. Youtube slams my 867Mhz Powerbook G4 cpu to playback video...

---

### Post by ivelasco on 2007-09-10
sudo apt-get update
sudo apt-get install mozilla-plugin-gnash

Now, plays youtube also

---

### Post by dynamicv on 2007-09-11
> **stmiller said:**
> There is an open source alternative for [PowerPC Linux users: Gnash]("https://wiki.ubuntu.com/PowerPCFAQ#head-b7d7a28d512999b3729800b8cd1cb796300111d8"). 
Many thanks for posting this.  Youtube performance in MOL has never really cut the mustard :)

---

### Post by wickstopher on 2007-09-12
Thanks for all the response.  Now I've got gnash 8.0 installed on my 15" TiBook, and mozilla-plugin-gnash, but flash pages are pretty garbled, and virtually unusable.  homestarrunner.com loads into 4 tabs for some reason, and I have yet to get a YouTube video to play.  Would it be advisable to upgrade to 8.1, or is it a lost cause on my older hardware?

---

### Post by rhetoric on 2007-10-09
> **wickstopher said:**
> Thanks for all the response.  Now I've got gnash 8.0 installed on my 15" TiBook, and mozilla-plugin-gnash, but flash pages are pretty garbled, and virtually unusable.  homestarrunner.com loads into 4 tabs for some reason, and I have yet to get a YouTube video to play.  Would it be advisable to upgrade to 8.1, or is it a lost cause on my older hardware?

I'm on an august 2005 edition ibook 1.33ghz having similar problems. Youtube videos (and player controls) are garbled to the point where it isn't worth watching. Package name "democracyplayer" is a standalone that allows you to search youtube, then downloads the flv and plays it. It works but it's a rather clunky annoying app... I'd like to figure out how to get mozilla-plugin-gnash to work with youtube at least. If anyone has a similar ibook could you please post your device= section from xorg.conf for your video card here so I can compare. Thanks

---

### Post by MisterRik on 2007-10-09
> **ivelasco said:**
> sudo apt-get update
sudo apt-get install mozilla-plugin-gnash

Now, plays youtube also

I somehow missed this the first time I read this thread. I tried it, and I got the following error message in Terminal:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by dmjones500 on 2007-10-19
Did you use the "sudo" command as suggested?

Are you in the sudoers group?

---

