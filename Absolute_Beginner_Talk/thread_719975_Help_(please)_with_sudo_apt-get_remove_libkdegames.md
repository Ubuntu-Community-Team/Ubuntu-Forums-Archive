---
title: "Help (please) with sudo apt-get remove libkdegames4-kde4"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-03-09
As I try to remove libkdegames4-kde4, I received the following error;

Package libkdegames4-kde4 is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kfourinline-kde4: Depends: libkdegames4-kde4 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specifya solution).

sudo apt-get -f install – returns 

0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Can anyone give me a suggestion how I can solve this problem?

Bill

---

### Post by JoshuaRL on 2008-03-09
Try:
```

sudo apt-get -f install
sudo dpkg --configure -a

```

You can also try going into Synaptic and the Broken Filter.  It should have all the broken packages in there to fix.

---

### Post by bmachia on 2008-03-09
Thanks Joshua
I tried your suggestions;
[INDENT]sudo apt-get -f install
[/INDENT][INDENT]sudo dpkg --configure -a
[/INDENT]
But still getting errors.  Please see below

bill@bill-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of kfourinline-kde4:
 kfourinline-kde4 depends on libkdegames4-kde4; however:
  Package libkdegames4-kde4 is not installed.
dpkg: error processing kfourinline-kde4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kfourinline-kde4

When I tried to Fix Broken packages with Synaptic, I get the following error;
E:/var/cache/apt/archives/libkdegames4-kde4_4%3a4.0.2-0ubuntu1~gutsy1~ppa1_i386.deb: trying to overwrite `/usr/lib/kde4/lib/libkggzgames.so.4.0.0', which is also in package kde4games

Any other thoughts?

---

### Post by JoshuaRL on 2008-03-09
You could try:

```

sudo apt-get install --reinstall kfourinline-kde4

```

BTW, how is KDE4 treating you otherwise?

---

### Post by bmachia on 2008-03-09
Thanks Joshua,
I found and fixed the problem.  It was a dependency from libkdegames4-kde4 that I could identify until you r suggestion of sudo dpkg --configure -a &  sudo apt-get install --reinstall kfourinline-kde4

Once I removed the dependency kfourinline-kde4 all ran fine.

In answer to your question, my install went smooth and all of the difficult things like ndiswrapper, remote printing just carried over from KDE3.  I would say its pretty good so far.

Well at least until to day when I tried to install some KDE4GAMES.  Thats when all started to fall apart.  And I had to come to the forum for the advice you offered.

Every now and then I like to run a Solitaire game, like Patience – it ran fine in KDE3, but not in KDE4, so I decided to install some KDE4 Card games.  I'll try something else later.  But for now – No Games.  I guess this could be the Boss's delight of upgrades.

Thank you very much
Bill

---

### Post by JoshuaRL on 2008-03-09
> **bmachia said:**
> I guess this could be the Boss's delight of upgrades.

Heh, nice.  So how fast is it?  And how does Compiz and other eyecandy do?

---

### Post by bmachia on 2008-03-10
Joshua
Its just as fast as KDE3.  I have noticed no slow-ness at all.  Rather nice.

As-far-as Compiz/Eyecandy; Widgiz's are extremely easy to add to the desktop, and then lock down.  The F9 function is no longer used, since everything is customizable via the desktop.  

My suggestion would be to install it over Gutsy, and at login switch between KDE3 or KDE4.  If you upgrade to Hardy, you would not have an opportunity to switch between the two and play with the differences.

Bill

---

