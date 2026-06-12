---
title: "How to transfer my current Ubuntu setup to another computer?"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by ThomThom on 2005-11-14
Hi.
I've just installed Ubuntu and have been playing around with it for a few days now. I have a good impression of it and I would like to install it on my old spare computer when I go back home for further testing. However, back home it's only a ISDN line so apt get-ing all the stuff I have installed here would take ages. Is there any way of transfering the current installation to a new installation on another machine?

---

### Post by lreyes6 on 2005-11-14
hi... 
you can burn all the deb files on /var/cache/apt/archives/ and make a local repository on your own computer on maybe in one with more capacity at home... read this [thread]("http://www.ubuntuforums.org/showthread.php?t=42862&highlight=repository+package+list")... i did one at home and works great...

hope this helps

---

### Post by ThomThom on 2005-11-14
And that won't copy any hardware spesific settings? The other computer's hardware is quite different. I've installed the ATI drivers on these, the other one got a builtin gfx card. Will that be copied as well and render the target system useless?

---

### Post by lreyes6 on 2005-11-14
no because if ubuntu doesn't need the ati drivers by example... ubuntu does not install it... with this you copy the packages not the configuration of your pc

maybe with this tip i give you the problem will be that you will need something that you don't have on your deb files but in that case you can download it at work from [here]("http://packages.ubuntu.com/") and copy them you your local repo

---

### Post by floppy on 2005-11-14
Are you trying to completely duplicate your system, including your menu setups, desktop, etc., or are you simply trying to make sure you don't have to apt-get a bunch of stuff all over again?

If the latter, you might want to look at this thread:
[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)
It'll show you an interesting way of creating your own repository of the applications you've already gotten, or of applications you might want sometime.

[Edit: sorry for duplicating the info about that thread; I was slow finishing my post :) ]

---

