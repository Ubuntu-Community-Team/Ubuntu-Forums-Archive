---
title: "How to go back to Feisty"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-10-19
Hi, I hate to be this person, but Gusty is just way to buggy for me. My computer is practically nonfunctional. I know it is probably possible to fix these issues, but there are just way too many and     I think I'll go back and upgrade when it has some updates. So, any way to go back to Feisty without losing my files? Thanks.

---

### Post by ///MVinny on 2007-10-19
Have one than one hard drive in your machine?  I'd mount it in gutsy, copy all the files/folders/directories to it that ya think you need, then start all over.

---

### Post by kevindubrow on 2007-10-19
Ehh, darn no, I may be able to get my hands on some blank CDs. I really want to avoid a fresh install, but that may be just what I have to do. This is honestly the first time I have been disappointed with Ubuntu. Seriously, it is causing my computer fan to spin backwards (no joke).

---

### Post by Malibu Illusion on 2007-10-19
This is why you should have two partitions, one mounted at / and the other at /home to preserve userdata between installs.

---

### Post by kevindubrow on 2007-10-19
I'll keep that in mind for the future. Thanks for the help, all.

---

### Post by ///MVinny on 2007-10-19
How about a USB thumbdrive?  How many 'files' is it that you're wanting to keep?

---

### Post by kevindubrow on 2007-10-19
Honestly I want to save all of my programs and maybe 20GB of files. It seems pretty hard to do without another hard drive. You see, Feisty gave me a lot of issues too and I will have to start all over again with it if I do a clean install. If I would have to do that, it may be easier to just keep Gusty even though it is so much worse for me than Feisty was.

---

### Post by R.Bucky on 2007-10-19
I know what you mean about Gutsy being buggy. It has got the best of me too. Certain applications do not work for me, but stick with it. I recently did the separate partitions for root and home drives. It works well and should be easier to fix any serious mistakes that I make when playing around. I highly recommend it. Think about purchasing an external harddrive for backing up your data. They are fairly cheap now. 

Good luck to you

---

### Post by kevindubrow on 2007-10-19
Thanks. I'll stay with Gusty for a few more days, hopefully they will make some updates.

---

### Post by ///MVinny on 2007-10-19
Do you have another computer on your home lan that has at least 20g of space?  You could install proftpd and just d/l all your files to the other machine.  Then wipe...

---

### Post by kevindubrow on 2007-10-20
I'll look into that, thanks a lot! If things don't change with Gusty for my model, I'll use that option to get back to Feisty.

---

### Post by ///MVinny on 2007-10-20
Good god man!  I wasn't ready to fall on the sword yet even on a test machine.  Sorry you're having so much trouble though, good luck!

---

### Post by TheWizzard on 2007-10-20
> **kevindubrow said:**
> Gusty is just way to buggy for me. 

you did file bug reports then, didn't you? filing bug reports is necessary in order to make ubuntu better.
if you want stability, stick to the lts versions. 

the easiest solution for you is to buy an external hdd. and in the future you'd better make a seperate partition for /home.

---

### Post by kevindubrow on 2007-10-20
I'll do that. And trust me, I give Ubuntu a lot of patience. I just need a working computer right now for school and I don't have one. I have to reinstall wireless every time I boot (but now that doesn't work, I am on a wired connection), the computer won't restart, audio suddenly stopped working, some programs are not working, my touch pad can not even be used, and until yesterday my cpu fan was spinning backwards! I love Ubuntu and I think the issues that I have after I upgrade every time are much easier to deal with than a day with Windows. I may try to back up as many files as I absolutely need onto a few CDs since I don't have an external drive right now and give Gusty another shot with a fresh install. I am being told that upgrades can be buggy...so lets see if these issues are just because of that. Thanks for the help everyone.

And about the separate partition thing, are you saying that I should make a 700MB partition for Ubuntu and leave the rest for /home? Thanks.

---

### Post by ArtInvent on 2007-10-20
There really needs to be an easier way to go back.

With my desktop box, I had an extra hard drive, 320GB, just like the one in the machine. Just before upgrading,  I made a clone of the Feisty disk using a live cd and the dd command. Then I could upgrade onto the clone, try it out for a few days, and if I don't like it, I can just pop the old drive in and be right back where I was. New hard drives are cheap, it was like $85. And being a SATA drive, the clone took all of 2 hrs. That's my new preferred way of just doing a general backup as well I think. 

However, I did decide to upgrade my old laptop without taking this same precaution, not having a spare drive on hand for it. There's not nearly as much stuff on the laptop, but I do wish I could go back to Feistiy. I have a few key apps as well that just don't work, and the glitzy desktop effects and other new functions in Gutsy really are too much of a load on the poor old girl.

In short, there is a way to upgrade, why can't there be a way in Synaptic to downgrade? Maybe there could be some kind of setting that makes the upgrade provisional and saves some info and data somewhere that Synaptic can use to restore the old system? You can do this for individual packages already, doing it for the whole system would be awesome. 

Keeping your home directory on a different partition saves a little bit of trouble - but no more than just copying your home to a USB hard drive after the fact. I've never liked keeping a separate partition because it seems I'm often running out of room on one partition and needing to resize or something, which is a pain. Plus, there are a lot of apps with a hidden partition and settings etc on the home directory. These are probably not going to be compatible in some instances with the old versions of those programs if you just pop them back with Feisty. And reinstalling from scratch - what's really a pain is reinstalling all your apps and settings, and customizations. You've got SSH set up a certain way, your menus, your networking, your xorg.conf, etc. I have a hell of a lot stuff like that and it would take week to redo it all. Say you have a lot of stuff working with Wine. Is this going to just work again once you've installed that using a later version of the OS. Maybe, maybe not. I really think that doing a disk clone is the only way to go on these distro upgrades, learned the hard way.

---

### Post by justinmiller87 on 2007-10-20
I'm going to have to agree with this one. If there's a minor kernel update, you get options to boot into either one under Grub, just in case something happens. The same should go for a complete upgrade.

I'm going to go toss this in the "Hardy Heron" idea pool.

---

### Post by EkakiJin on 2007-10-20
I can't believe something as high of quality as, well anything linux, isn't able to revert to an older version without a re-install. -_-()

I just upgraded (saw "version 7.10" when I had 7.04 [I think], and no notice it was so different they even changed the name, and installed it), and the damned thing has completely eaten my Beryl. <_<  I can't even find it to try to turn it back on, and even though I can still supposedly log into a beryl session, it won't let me utilize anything but xgl (it notified me after I upgraded, and started freaking out because Beryl had not only stopped working, but wasn't even available as an icon).

What kind of upgrade tells you what you should run??? :mad: 

At this point I can barely imagine being on anything but linux, but this "gutsy" version is ridiculous!

---

### Post by Frak on 2007-10-20
I would back up and reinstall Feisty, there is no way to downgrade.

---

### Post by EkakiJin on 2007-10-20
Is there any way to at least get Compiz Fusion to start working?  It's forced me into xgl, even though I know my computer is more than capable of running Compiz....

---

### Post by Frak on 2007-10-20
> **EkakiJin said:**
> Is there any way to at least get Compiz Fusion to start working?  It's forced me into xgl, even though I know my computer is more than capable of running Compiz....
[http://elemongw.exofire.net/blog/2007/10/6/git4cf-automator-version-0.1-beta-2](http://elemongw.exofire.net/blog/2007/10/6/git4cf-automator-version-0.1-beta-2)

---

### Post by EkakiJin on 2007-10-20
I just downloaded it, but I have no idea how to get into root, since the person who gave me Ubuntu and showed me a little (tiny bit) about that didn't really show me how to get into it.... -_-()

In other words: I have no idea how to install it.  Sorry. -_-

---

### Post by kevindubrow on 2007-10-21
There are a lot of things that Ubuntu is lacking, I still would take it over any other OS though! I would very much like to see a way to downgrade in a later version or maybe an update to this version!

---

### Post by jdong on 2007-10-21
There is currently no supported downgrade path; it is a technical limitation of APT and the packages. There's often one-way migration scripts built into packages but the reverse way is unimplemented.

I think it is a worthwhile usecase / feature request but to be honest it seems like so much work I don't think it'll happen.

---

### Post by Frak on 2007-10-21
> **jdong said:**
> There is currently no supported downgrade path; it is a technical limitation of APT and the packages. There's often one-way migration scripts built into packages but the reverse way is unimplemented.

I think it is a worthwhile usecase / feature request but to be honest it seems like so much work I don't think it'll happen.
It could happen, but 5 people on the job, plenty of pay, 3 years, and we have just reached perpetual Alpha.

---

