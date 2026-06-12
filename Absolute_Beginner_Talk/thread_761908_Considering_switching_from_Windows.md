---
title: "Considering switching from Windows"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by paranoir on 2008-04-21
Vista, to be specific. It's not *quite* as bad as most people make it out to be, but it's no XP. So, I've been strongly considering this for a while now, and I think I'm ready to try it.  I *have* tried Ubuntu back when 7.10 first came out, and now with 8.04 and some nice new features, I'm interested again. But this time, I'm doing a little more research ;) I have a few questions that some of which I'm sure have been asked before, so try to forgive me.

I'm more computer savvy than the average Windows user, but I'm a noob in new territory, and I get nervous I'm gonna screw something up. Please bear with me x)

- I want to set up a dual-boot between Vista and Ubuntu. I want to use Ubuntu as my main OS, but have Vista stored away for some things. So, my question is: burning everything to a DVD aside, is there an easy way to share my files (pictures, music, videos) between the two? If so, how?

- I'm gonna use wubi at first, but if I really dig it, I'll likely install it for real. Should I want to upgrade or try another distro or something in the future, how would I go about not losing all my stuff? Partitions confuse the hell out of me, but I'm pretty sure setting up a separate /home is what I'm looking for. But how would I go about *that?*

- I play World of Warcraft, and with a, er...nice amount of add-ons ;) Heh. Aside from getting it to run in Wine and all that, is there anything I should know that would be different? Particularly about downloading and installing add-ons. WoW runs nicely alone from what I've heard, but I do so love my add-ons.

- Also, installing WoW. How would one do that? And would I even need to, or can that be shared between Ubuntu and Vista, too? That would be one hell of a time saver, heh.

Answers and help are greatly appreciated. I sincerely apologize if the answers for these are floating around already, but I really have looked into them before and didn't really find the sort of answers I was looking for. If you need to know anything about my computer to better answer, just ask away.

---

### Post by cotcot on 2008-04-21
> **paranoir said:**
> 

- I want to set up a dual-boot between Vista and Ubuntu. I want to use Ubuntu as my main OS, but have Vista stored away for some things. So, my question is: burning everything to a DVD aside, is there an easy way to share my files (pictures, music, videos) between the two? If so, how?

- I'm gonna use wubi at first, but if I really dig it, I'll likely install it for real. Should I want to upgrade or try another distro or something in the future, how would I go about not losing all my stuff? Partitions confuse the hell out of me, but I'm pretty sure setting up a separate /home is what I'm looking for. But how would I go about *that?*.

You can share files on FAT or EXT3 partitions. Linux can even read NTFS.
Windows needs the [[COLOR="Red"]fs-driver[/COLOR]]("http://www.fs-driver.org/") to read ext3.

Just dual boot : ubuntu after vista. [[COLOR="Red"]Here[/COLOR]]("http://www.users.bigpond.net.au/hermanzone/") is a description how to do.

---

### Post by aktiwers on 2008-04-21
1) You can do that when you install the OS. Just pick Manual partitioning and create: 

A partition in EXT3 format with mountpoint /  (about 5-10gb would do to start with or more if you like).
A partition in EXT3 format with mountpoint /home (make it the size you like, I would say 4-10gb also) depending on how much you will use it.
A partition mounted as SWAP. (I have this on 1gb) It will work as reserve for Memory.

Install EXT3 driver in Windows.

2) I don't think you can share files between a wubi install and Windows.

3)WOW should work in either Cedega or Wine

4) Cedega would be easiest, but here is a Wine howto:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Actually I think Wine-doors will download and install it for you automatically.
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

Hope that helps - good look and welcome.

---

### Post by indiecast on 2008-04-21
1.  If you have all of your files backed up, you can't screw anything up.  I'm not going to lie...Linux is very different territory, and it was pretty confusing to me first. Once i read the simple getting started guide that comes with the OS (a very smart descision), i was fine for the most part.

2.  If Vista is already installed the way you want it to be installed, adding ubuntu to your combination is a breeze, just make sure you back up your personal stuff.  Then just run the installer and follow the directions.  After installation, Ubuntu should automatically mount your vista partition and you should easily be able to access all of your files :)

3.  Upgrading Ubuntu is a breeze.  When a new version comes out the update manager will handle all of that for you.  Making a /home partition is a great idea and i wish i would have thought to do that.  The Ubuntu installer makes that very easy.

4.  WoW does work in WINE i believe. I haven't done much gaming lately, but i kinda have a feeling that it's best to play games on the platform they were designed for.  So you may or may not want to stick with playing it on Windows after trying it on WINE.

5.  You might be able to share WoW between Windows and Ubuntu...not sure.


hope this helps, and if you have any further questions, feel free to ask,

IndieCast

---

### Post by Michael.Godawski on 2008-04-21
Installation Guides:
[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[*][http://apcmag.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[/LIST]

For separate Home:
[LIST]
[*][http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[/LIST]

---

### Post by indiecast on 2008-04-21
> **aktiwers said:**
> 

2) I don't think you can share files between a wubi install and Windows.



Yes you can...I do it all the time

---

### Post by aktiwers on 2008-04-21
> **indiecast said:**
> Yes you can...I do it all the time

Ahh ok.. never used it really ;)
But thanks for clearing it out.

---

### Post by eriqjaffe on 2008-04-21
> **aktiwers said:**
> 2) I don't think you can share files between a wubi install and Windows.Your C: drive should be visible at /host.  At least, my XP box works that way.  According to the WUBI folks, other partitions/drives should be visible in /media, but I had to manually add two other drives (secondary IDE and a SCSI drive) to /etc/fstab to get them to show up.  No big deal.

I created a symbolic link to /host in /media so that I can get to all of my drives there.

I'm not so sure about accessing your Linux install when you're in Windows, there may be some way of mounting the WUBI disk, but there isn't one that I'm aware of.

---

### Post by indiecast on 2008-04-21
np... all partitions except swap are mounted into the filesystem :)

---

### Post by indiecast on 2008-04-21
> **eriqjaffe said:**
> Your C: drive should be visible at /host.  At least, my XP box works that way.  According to the WUBI folks, other partitions/drives should be visible in /media, but I had to manually add two other drives (secondary IDE and a SCSI drive) to /etc/fstab to get them to show up.  No big deal.

I created a symbolic link to /host in /media so that I can get to all of my drives there.

I'm not so sure about accessing your Linux install when you're in Windows, there may be some way of mounting the WUBI disk, but there isn't one that I'm aware of.


its normally much easier than that

and xp can see ubuntu with a special driver, but not naturally

---

### Post by aktiwers on 2008-04-21
> **indiecast said:**
> np... all partitions except swap are mounted into the filesystem :)

I meant from Windows accessing Ubuntu

---

### Post by SlappyPappy on 2008-04-21
Vista is freaking brutal and XP and no joy either. I've been helping people remove Vista and get back to XP. A really painful experience for people, big time driver problems.

This weekend I was fixing a friends computer that had over 90 viruses. Yeppers, that's 90 viruses. It was nothing short of amazing that thing was still running, or barely running.

Linux is the way to go, that or get a Mac. PCs are a flipping joke these days. I feel sorry for people who can't fix them. They must be dumping good machines just to get away from their problems!

As a beginner I've been hanging out in this forum and reading just about everything and trying to get a handle on what people are saying. It's a bit like drinking from a fire hose but I'm learning a ton. I'm now running Ubuntu full time and not missing a thing from my PC, yet!   :mad:

---

### Post by indiecast on 2008-04-21
> **aktiwers said:**
> I meant from Windows accessing Ubuntu


ohhhhhhhhhhh lol oops.  yeah windows can see but it needs special driver or something

---

### Post by sneeks on 2008-04-21
> **SlappyPappy said:**
> Vista is freaking brutal and XP and no joy either. I've been helping people remove Vista and get back to XP. A really painful experience for people, big time driver problems.

This weekend I was fixing a friends computer that had over 90 viruses. Yeppers, that's 90 viruses. It was nothing short of amazing that thing was still running, or barely running.

Linux is the way to go, that or get a Mac. PCs are a flipping joke these days. I feel sorry for people who can't fix them. They must be dumping good machines just to get away from their problems!

As a beginner I've been hanging out in this forum and reading just about everything and trying to get a handle on what people are saying. It's a bit like drinking from a fire hose but I'm learning a ton. I'm now running Ubuntu full time and not missing a thing from my PC, yet!   :mad:

i know where your coming from mate,downgrading to xp is a bugger for a lot of new machines.
i try to get them to have ubuntu if possible and most get on quite well.
have got two boxes running for myself at home just to ease the family in,but son has ubuntu full time and he aint broke it yet after 4 months.
its just some nitty gritty stuff thats a pain,but will get on with it.

---

### Post by paranoir on 2008-04-21
Oh man, thanks guys :) Using wubi now. Getting all my stuff to work here was actually...pretty easy. Well, didn't try WoW yet, but I'm sure that won't be too bad.

Wubi seems pretty solid. What're the advantages of a full install, though? Silly question, I know.

Also, Firefox question! Is there a way to switch tabs by pressing ctrl + a number, like in Windows? Like, ctrl+1 goes to the first tab, 2 the second, 3 the third, etc. This is probably a really dumb question, but I didn't see it in the options :| Heh.

And, one last thing, and silliest of all. There a way to get .NET framework working in this, or is that a no-go? No biggie either way.

Thanks again :)

...Oh, that's weird. The forum smilies aren't showing up for me >_> Hm. Is that 'cause of the maintenance they just did?

---

### Post by ace007 on 2008-04-21
From [_[COLOR="Blue"]Wubi FAQ[/COLOR]_]("http://wubi-installer.org/faq.php")...

**What is the performance?**

*The performance is identical to a standard installation, except for hard-disk access which is slightly slower. If your hard disk is very fragmented the performance will degenerate. However, once the Ubuntu install created by Wubi has been transferred to a dedicated partition using LVPM, the hard drive access speed will be identical to that of a standard Ubuntu installation.*

---

### Post by eriqjaffe on 2008-04-22
It **may** be possible to get .NET running through Wine, although I haven't tried it myself.

---

### Post by indiecast on 2008-04-22
why would you need the .NET framework?

---

### Post by paranoir on 2008-04-22
> **indiecast said:**
> why would you need the .NET framework?

[http://www.wowace.com/wiki/WinAceUpdater](http://www.wowace.com/wiki/WinAceUpdater)

Like I said, silly and not a big deal :P Just trying to see how lazy I could be. Hah.

---

### Post by indiecast on 2008-04-22
ohhh that's right... the add ons

---

