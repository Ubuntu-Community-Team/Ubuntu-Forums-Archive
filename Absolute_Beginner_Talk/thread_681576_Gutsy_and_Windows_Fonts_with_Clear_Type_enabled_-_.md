---
title: "Gutsy and Windows Fonts with Clear Type enabled - please tell me how!?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by wyslij on 2008-01-29
Hello!

I've searched all the forums and still couldn't find an answer.

I have just installed the Gutsy 7.10 and also installed the MS fonts and copied even Tahoma font from my windows installation.

The fonts work fine... but there is no clear-type effect for them on web pages. I have a laptop with a nice LCD screen and kinda gotten used to having nice clear-type effect on the fonts and can't work in Ubuntu without this.

I have read about David Turner's patch and all this stuff, but it seems it only works for earlier versions of Ubuntu (Feisty).

Please, if you can, help me out here and let me know how to enable the cleartype effect on MS Windows fonts like Verdana, Tahoma or Times New Roman in my Ubuntu installation so that when I view the web pages in Linux, they look the same great as in Windows?

I really need that. I'm used to clear type after so many years with Windows - now I want to jump on Ubuntu bandwagon but if my MS fonts can't have cleartype effect (or any other anti-aliasing effect) than I'll have to skip it.

BTW - other fonts that came with Linux have the cleartype effect without a problem. Just the MS Winodws fonts are not.

Please help - I'm a Linux newbie.

---

### Post by jpeddicord on 2008-01-29
Moved from Tutorials and Tips.

---

### Post by emarkd on 2008-01-29
ClearType is involved with some of the Microsoft patent issues.  Here's a succinct writeup about the issue:  [http://boycottnovell.com/2007/04/08/patent-font/](http://boycottnovell.com/2007/04/08/patent-font/)

The closest you can get in Ubuntu is to click on System > Preferences > Appearance and select the Fonts tab.  At the bottom, check the box for Subpixel Smoothing

---

### Post by wyslij on 2008-01-29
I heard about that patent issue, but I thought that someone posted an unofficial way of making Verdana and other MS Fonts antialiased.

I found this:

[http://pimpyourlinux.com/linux-feature-review/pimp-out-your-fonts-for-linux/](http://pimpyourlinux.com/linux-feature-review/pimp-out-your-fonts-for-linux/)

So it seems it's do-able... I'm just a newbie and I have Gutsy and the info on this page is out-dated I guess...

I've installed Windows fonts and they are the only fonts that are not antialiased so my web pages look strange with some fonts antialiased and some not... especially I need Verdana, Tahoma and Times New Roman to be antialiased.

Can you help?

---

### Post by emarkd on 2008-01-29
That info is very outdated and you shouldn't use it.  I followed a few of the links off of there and came to this information for Gutsy:  [http://ubuntuforums.org/showthread.php?t=489326](http://ubuntuforums.org/showthread.php?t=489326).  Be aware that this was put out before Gutsy was finalized and according to the information there, even that is now outdated and the Fonts tab in the Appearance dialog is the preferred way to configure your font rendering, but you may find some information by reading through the thread.

---

### Post by hugmenot on 2008-01-29
Everything you need is installed in Gutsy by default. This is why all instructions you find are outdated. No need to install anything. Just go into the "Details" section of the font preferences and enable "Subpixel".
The hinting level is up to your taste.

---

### Post by wyslij on 2008-02-01
True - it was there - I just used the info with XML files and stuff and it was not necessary.

So - if you want to have Windows fonts - just install them and don't twak anything and they will work well and totally clear-typed...

Thanks for the help guys! Enjoying my Ubunut now!

---

### Post by dcstar on 2008-02-02
> **emarkd said:**
> **That info is very outdated and you shouldn't use it**.  I followed a few of the links off of there and came to this information for Gutsy:  [http://ubuntuforums.org/showthread.php?t=489326](http://ubuntuforums.org/showthread.php?t=489326).  Be aware that this was put out before Gutsy was finalized and according to the information there, even that is now outdated and the Fonts tab in the Appearance dialog is the preferred way to configure your font rendering, but you may find some information by reading through the thread.

Moral for all Ubuntu users who consider themselves "Absolute Beginners":

Do** NOT** follow any instructions unless they specifically say that they work on **YOUR** version of Ubuntu.

---

