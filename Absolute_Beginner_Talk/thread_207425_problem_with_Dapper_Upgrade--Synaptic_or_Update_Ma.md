---
title: "problem with Dapper Upgrade--Synaptic or Update Manager"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by olivesmarch4th on 2006-07-01
I just installed Ubuntu Breezy today (got it with the book "Beginning Ubuntu Linux'), after failing rather colossally with Linspire.  My experience with Linux is pretty much limited to today and yesterday.

I LOVE Ubuntu, it's gorgeous.  I had some initial problems with wireless but it seemed to resolve itself.  I'm online now, and as far as I'm concerned that seals the deal.

I want to upgrade to Dapper.  The typical suggested method, i.e. through Update Manager, doesn't work.  It shows "Your System is Up-to-Date!", then when I press reload, I get a pop-up box that announces that a New Upgrade is Available, but with no option to install it.  Instead, it directs me to the Ubuntu website.

Going through Synaptic Packages Manager doesn't work, either.  If I click "Mark All Upgrades", nothing happens, and the "apply" button is greyed out and unusable.

So my final recourse, according to the Ubuntu website, is to do everything manually through the Terminal.  I did what it asked me to do, but after password entry the terminal gave me a message saying the Authentication Process has failed because the system doesn't support such authentication protocol.

Weirdly enough, I still got my source information in a kind of text file, and I edited it per the instructions on the site, saved the text file and attempted to go through with the upgrade anyways.

And... rather predictably, I screwed up EVERYTHING.  I tried to change it back but Synaptic still couldn't read the CDROM stuff and I was getting error messages left and right.  Changing all the "dapper"s back to "breezy"s to try to restore the damage I had done also failed.

Given my extremely limited experience with Linux, or command-based anything, and considering that I had no idea what I had just done, I decided to completely reinstall Ubuntu Breezy.

Now the install has restored everything back to the way it originally was, but I am afraid to touch anything after messing with the source code like I did and having that fail.

Examining "Synaptic", it appears that I don't have the latest version of the Upgrade Manager, but I have no idea how to obtain it, or if having it would allow me to then upgrade the "easy" way.

Any direction one would like to give on this matter would be most appreciated.  I'm not touching a damn thing until I get some advice.

Thank You Very Much,
Christy

---

### Post by TwistesdTexan on 2006-07-01
I don't know if this will help bu there is a link to save you a lot of trouble in the Wiki. You might also want to know that I have seen a few people that had to stick with the i386 version because of confilcts. That will also be covered in the Wiki guide. The following link will help you if you read several of the links. Synaptic upgrade is the easiest to me and the least problems. 

[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Best of luck with your upgrade and if I can help I will try.

---

### Post by olivesmarch4th on 2006-07-01
Thanks for the link!

I MAY  have found the solution... I won't know for sure until my updates complete, but I reached a point in my guidebook that said to "Set Up Software Repositories" in Synaptic.  I did, and... viola!  All the sudden there were a ton of new updates to install, and at present are doing so...

We'll see how it goes.  God this is such a wonderful OS.

---

### Post by olivesmarch4th on 2006-07-01
Well, enabling the software repositories fixed the updating problem...

But ultimately I get an error message (at the end of the upgrade) that states:

"After your package information was updated the essential package "ubuntu base" cannot be found anymore.  This indicates a serious error.  Please report this as a bug."

I went to report it, but it's already been reported.  So I guess I just sit back and wait until the issue is addressed, if it ever is...  In the meantime, I'm happy with Breezy. :)

---

