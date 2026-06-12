---
title: "How can we install fluxbox and enlightenment?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-05-29
i am having ubuntu 7.04. I want to install these two window managers. how can i do that. when i searched in package manager it is not displaying anything.

---

### Post by yabbadabbadont on 2007-05-29
Make sure that you have the universe and multiverse repositories enabled.  In synaptic, Settings->Repositories.  Enable the extra ones and save the changes.  Now hit the reload button.  At least fluxbox should be there now.

---

### Post by Tux Aubrey on 2007-05-29
Last time I checked there was a fairly recent version of Fluxbox in the universe repositories.  It installed as a very empty WM (no menu entries etc) so be prepared to configure it.

Enlightenment was there too - but only the older, stable E16.  You have to install E17 from source I think.

---

### Post by RedSquirrel on 2007-05-29
> **Tux Aubrey said:**
> Last time I checked there was a fairly recent version of Fluxbox in the universe repositories.  

It's actually a little old now, but still quite usable. It's 1.0rc2. The Fluxbox developers have released 1.0rc3. The latter must be compiled, however.

> **Tux Aubrey said:**
> It installed as a very empty WM (no menu entries etc) so be prepared to configure it.

The menu problem can be fixed by running the following in terminal, immediately after one installs Fluxbox:

```
sudo update-menus
```> **Tux Aubrey said:**
> Enlightenment was there too - but only the older, stable E16.  You have to install E17 from source I think.Here is a HOWTO that uses third-party repositories:

[URL="http://ubuntuforums.org/showthread.php?t=319336"]How To Install Enlightenment E17 Using The Elbuntu Repositories
[/URL]
(I haven't tried it myself.)

---

### Post by Brunellus on 2007-05-29
the Fluxbox Howto in my .sig file will give you everything you need to know about Fluxbox in ubuntu.

---

### Post by shen-an-doah on 2007-05-29
> **Brunellus said:**
> the Fluxbox Howto in my .sig file will give you everything you need to know about Fluxbox in ubuntu.

Have you thought about adding some stuff about using Rox with Fluxbox? It can be pretty useful. It can be a nightmare trying to find a guide about setting it up though. I eventually found [this](http://forums.debian.net/viewtopic.php?p=26103#26103), which worked perfectly.

---

### Post by Brunellus on 2007-05-29
> **shen-an-doah said:**
> Have you thought about adding some stuff about using Rox with Fluxbox? It can be pretty useful. It can be a nightmare trying to find a guide about setting it up though. I eventually found [this](http://forums.debian.net/viewtopic.php?p=26103#26103), which worked perfectly.
I try to keep the wikipage to Fluxbox only.  If you want to add a new wikipage on Flux with Rox, go on ahead. 

Personally, if I use Fluxbox, it's as a part of a super-minimal install that doesn't usually need much GUI anyway...it's faster just to open up a bunch of xterms.

---

### Post by shen-an-doah on 2007-05-29
> **Brunellus said:**
> I try to keep the wikipage to Fluxbox only.  If you want to add a new wikipage on Flux with Rox, go on ahead. 

Personally, if I use Fluxbox, it's as a part of a super-minimal install that doesn't usually need much GUI anyway...it's faster just to open up a bunch of xterms.

Ooh, didn't know I could do that. I'll look into it.

---

### Post by BLTicklemonster on 2007-05-29
So does the link for installing e17 with ebuntu repos work with feisty? I haven't used e17 in a while, and keep thinking about putting it on again.

---

### Post by RedSquirrel on 2007-05-30
> **shen-an-doah said:**
> Have you thought about adding some stuff about using Rox with Fluxbox? It can be pretty useful. It can be a nightmare trying to find a guide about setting it up though. I eventually found [this]("http://forums.debian.net/viewtopic.php?p=26103#26103"), which worked perfectly.

Here is another guide for rox written by bodhi.zazen (he says it is a modified version of the one on Debian forums):

[How-to rox like an expert]("http://community.fluxbuntu.org/index.php?topic=78.0")

---

### Post by RedSquirrel on 2007-05-30
> **BLTicklemonster said:**
> So does the link for installing e17 with ebuntu repos work with feisty? I haven't used e17 in a while, and keep thinking about putting it on again.
I haven't tried it because I'm happy with my Fluxbox SVN, but there are feisty repositories in that HOWTO, and here is at least one [satisfied customer]("http://ubuntuforums.org/showpost.php?p=2637420&postcount=222") who uses feisty. :)

---

### Post by yabbadabbadont on 2007-05-30
> **RedSquirrel said:**
> I haven't tried it because I'm happy with my Fluxbox SVN

My fluxbox SVN is newer than your fluxbox SVN...    Na, na, na, na, na.   :lol:

---

### Post by RedSquirrel on 2007-05-30
> **yabbadabbadont said:**
> My fluxbox SVN is newer than your fluxbox SVN...    Na, na, na, na, na.   :lol:

That was bound to happen. I only update once a week (usually). I might have to change my policy just to keep up with the ... ... yabbadabbadonts. :lol:

Did you have any trouble with the compilation? I've had some seemingly random segmentation faults. I was going to try different compiler flags, but I got it to work  just by trying 'make' again. Weird. I also grabbed fresh source rather than doing 'svn update', and that made it work. :confused:

---

### Post by yabbadabbadont on 2007-05-30
I just restaged the machine, so it was a fresh set of source for me too.  No problems building it though.  From my years of experience using Gentoo, I can tell you that random seg faults while compiling generally mean failing hardware somewhere....  :(  (or worse, a broken tool chain)  You might want to run the memory test at boot.  If you aren't already, you probably should run a temp monitor to be sure that the system isn't overheating during the build.

The code is so small, that I plan on just wiping the build tree and pulling down the full source every time I build a new version.  "svn up" should work, but I've run into build problems with it on other packages before.  Never with Fluxbox though.  Anyway, better safe than sorry.  ;)

---

### Post by RedSquirrel on 2007-05-31
Thanks for the tips.

This machine has done an enormous amount of compiling in the past with no difficulty. I checked the memory and it's OK. Monitoring the temperature is tricky because the motherboard has a buggy BIOS. I'm not entirely convinced that an overheated system is the cause since it hasn't been an issue before...

What are you compiling on? feisty? I have feisty server.

I may play around with this some more, but I like it better when it "just works". :mad:

---

### Post by yabbadabbadont on 2007-05-31
> **RedSquirrel said:**
> What are you compiling on? feisty? I have feisty server.

I used the feisty minimal net installation image.  It's only 10mb and does an install by pulling everything down from the repos.  I actually do an expert install and stop before it is truly "finished".  I never do the "select and install software" step.  This leaves me with a command line system that has ubuntu-minimal on it.  I then install ubuntu-standard (which is still command line).  Then I replace upstart with the standard sysvinit.  (I just like it better)  Next I remove a few packages that are included in those two meta-packages that I don't want or need.  (wireless tools and such)  Finally, I install xorg, a bunch of development tools and libraries, browser, e-mail client, and a few audio/visual apps.  Then I build fluxbox.

---

### Post by SAMW on 2007-05-31
Wow, um I just followed the e17 install link and i did everything, but it installed e16:-|

It looks like this:

[http://upload.wikimedia.org/wikipedia/en/c/cd/Screenshot_enlightenment_large.png](http://upload.wikimedia.org/wikipedia/en/c/cd/Screenshot_enlightenment_large.png)

without all the special stuff (sorry, don't know how to screeshot in enlightenment)

---

### Post by RedSquirrel on 2007-05-31
> **yabbadabbadont said:**
> I used the feisty minimal net installation image.  It's only 10mb and does an install by pulling everything down from the repos.  I actually do an expert install and stop before it is truly "finished".  I never do the "select and install software" step.  This leaves me with a command line system that has ubuntu-minimal on it.  I then install ubuntu-standard (which is still command line).  Then I replace upstart with the standard sysvinit.  (I just like it better)  Next I remove a few packages that are included in those two meta-packages that I don't want or need.  (wireless tools and such)  Finally, I install xorg, a bunch of development tools and libraries, browser, e-mail client, and a few audio/visual apps.  Then I build fluxbox.

Thanks for that info. When I decided to try feisty, I wiped the hard drive and fired up that net installer. I poked around a little, and there certainly is lots of room for customizing what is installed. I decided to go with a LAMP server this time, but maybe next time I'll try something else. 

I got SVN 4916 to work by lowering the compiler optimization a bit. Not the ideal solution, perhaps, but I haven't seen any ill effects so far. [-o< 8-[

---

