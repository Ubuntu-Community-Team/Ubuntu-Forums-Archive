---
title: "Preparing for Hardy Upgrade"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2008-02-19
I recently upgraded from Feisty to Gutsy.  However, to do that I tried an upgrade option which turned out to be a disaster. The next time I plan on doing a fresh install...

What is the quickest way of backing and restoring the desktop look in Gnome?

Is it backing up my whole home folder and pasting it into Hardy right after install?  Will this work? I doubt this a little as by the time Hardy is ready new versions of software apps will be released so to me using old settings will mess things up. 

Maybe I should back up only a few things.  Foremost, I would like to have the Gnome desktop look preserved without spending time to recreate it.

Thanx.

---

### Post by seventhc on 2008-02-19
When HARDY comes out it shouldn't be a problem to just upgrade, what was the disaster?
Backing up your home folder is a good idea no matter what and it should restore you theme.
But you should be able to do the upgrade also.
I do backup my home folder but I don't restore everything, but I do have the themes files I need, so I just reinstall them. It takes like 1 minute to do.
I don't use compiz or anything though so maybe that takes longer, I basically have 4 .tar.gx files that I install for my theme

---

### Post by dcstar on 2008-02-19
> **bagrol1 said:**
> I recently upgraded from Feisty to Gutsy.  However, to do that I tried an upgrade option which turned out to be a disaster. The next time I plan on doing a fresh install...

What is the quickest way of backing and restoring the desktop look in Gnome?

Is it backing up my whole home folder and pasting it into Hardy right after install?  Will this work? I doubt this a little as by the time Hardy is ready new versions of software apps will be released so to me using old settings will mess things up. 

Maybe I should back up only a few things.  Foremost, I would like to have the Gnome desktop look preserved without spending time to recreate it.

Thanx.

Everybody - repeat everybody - should have a separate /home partition.

If you have such a thing, installing or upgrading Ubuntu versions will mean that all of your data (including desktop configuration) is preserved.

Sometimes things like a new Gnome version will cause files to be upgraded to a new format, but at least you retain what you had previously.

With a separate /home all you do is either specify where it is during the partitioning phase of a fresh install, or switch over to using it after an install has completed and you are happy everything works ok on the system.

I don't really understand why Ubuntu doesn't create/use a separate /home by default, it would save a lot of new users grief when they reinstall (for whatever reason) and find that they have just wiped out their previous /home data which was in the old root partition.

---

### Post by seventhc on 2008-02-19
I agree with having a separate home folder, but it isn't something I started doing until recently.
I still back it up though, just in case.

---

### Post by bodhi.zazen on 2008-02-19
Well, not to be completely controversial, I do NOT like a separate /home. There are a number of config files in /home that do not need to be backed up at all and can conflict across distros.

Personally I use a /data partition and link to /home: 

ln -s /mnt/data/music /home/<user>/music

And on ....

At any rate to answer the OP, there really is nothing you need to do to prepare for 8.04. You should already be backing up your data and when the time comes you will update or re-install as you wish.

Updating ANY OS, Ubuntu or otherwise, can be problematic.

---

### Post by r4ik on 2008-02-19
Since Hardy is a LTS my option is a fresh install.

---

### Post by wolfen69 on 2008-02-19
> Everybody - repeat everybody - should have a separate /home partition.
i agree with bodhi. why should ***everyone*** do it that way? i personally keep all important data on seperate hard drives. so re-installing is no big deal. just backup any files you want to keep, and go for the fresh install. no biggie.

> bodhi.zazen:
Updating ANY OS, Ubuntu or otherwise, can be problematic.
that's why i never would consider upgrading.

---

### Post by dcstar on 2008-02-19
> **wolfen69 said:**
> i agree with bodhi. why should ***everyone*** do it that way? i personally keep all important data on seperate hard drives. so re-installing is no big deal. just backup any files you want to keep, and go for the fresh install. no biggie.
...........

Ok, here's some good reasons:

[LIST=1]
[*]No /home data will be wiped out by reinstalling Ubuntu.
[*]In the event of any sort of power issue, corruption to the /home partition will not affect the root partition, and vice-versa.
[*]You won't crash your system by filling the /home partition (as can happen if it is part of the root partition).
[*]You can even run multiple versions of Ubuntu sharing the same separate /home partition.
[/LIST]
Compared to the "advantages" of leaving /home in the root file system (are there any at all?), I reckon that list is compelling.

---

### Post by Antidisestablishmentarian on 2008-02-20
Sort of a nooby question, but how do we create a partition in Ubuntu? I know how to do it in Windows, but not Ubuntu.

---

### Post by articpenguin on 2008-02-20
whats the benefit of /usr?

---

### Post by bodhi.zazen on 2008-02-20
> **dcstar said:**
> Ok, here's some good reasons:

[LIST=1]
[*]No /home data will be wiped out by reinstalling Ubuntu.
[*]In the event of any sort of power issue, corruption to the /home partition will not affect the root partition, and vice-versa.
[*]You won't crash your system by filling the /home partition (as can happen if it is part of the root partition).
[*]You can even run multiple versions of Ubuntu sharing the same separate /home partition.
[/LIST]
Compared to the "advantages" of leaving /home in the root file system (are there any at all?), I reckon that list is compelling.

Well, with a data partition I have all those advantages as well with the additional advantage  that I can share the /data partition across multiple distros.

By keeping /home on / the config (dot) files in /home never conflict. There are numerous potential conflicts, even if you stay with Ubuntu. What if you run Kubuntu / Xubuntu / and Ubuntu, or one install with Beryl and another with Compiz, and yet a third with that stuff disabled ? Now add a second distro, like Centos/Fedora, and before you know it your config files in your shared /home are causing all kinds of problems.

You see, we all have our reasons, which is what wolfen69 was saying as well. It is nice to have freedom and choice.

---

### Post by bodhi.zazen on 2008-02-20
> **Antidisestablishmentarian said:**
> Sort of a nooby question, but how do we create a partition in Ubuntu? I know how to do it in Windows, but not Ubuntu.

IMO it is best to partiton from a live CD. Boot your Ubuntu desktop CD and run the application Gparted.

Gparted is on the desktop (live CD) but is not installed by default.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by bodhi.zazen on 2008-02-20
> **articpenguin said:**
> whats the benefit of /usr?

Are you asking for an overview of the Filesystem tree an function of /usr ?

[http://ubuntuforums.org/showthread.php?&t=258611](http://ubuntuforums.org/showthread.php?&t=258611)

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

Or are you asking about any potential advantage of putting /usr on a separate partition ?

---

### Post by bagrol1 on 2008-02-20
OK, that sounds reasonable to have /home at seperate partition.

Another way I may add is to have /home on a separate hard drive.  This is the way I would like to contemplate more on. 

How do I do it?  How do I make Ubuntu see /home on a different drive making this drive to be mounted automatically, and etc.

Thanx!

---

### Post by bodhi.zazen on 2008-02-20
> **bagrol1 said:**
> OK, that sounds reasonable to have /home at seperate partition.

Another way I may add is to have /home on a separate hard drive.  This is the way I would like to contemplate more on. 

How do I do it?  How do I make Ubuntu see /home on a different drive making this drive to be mounted automatically, and etc.

Thanx!

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

