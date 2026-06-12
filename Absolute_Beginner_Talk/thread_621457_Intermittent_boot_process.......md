---
title: "Intermittent boot process......"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by truthbrush on 2007-11-23
I am a few weeks into getting my dual boot system working and have hardly touched Win XP.

Everything was running A1OK on Gutsy, however I have 1 problem that occured mid week and I have started fixing tonight.

I am running XP Pro on hda and Gutsy on hdb as a dual boot.

The grub booted fine until the last round of updates I installed and then I got an error in Grub 1.5 ('Error 18').....I have googled and discovered about /boot partition size but that gives me 3 problems......both drives are 160GB and the Gutsy drive is partitioned as follows.....

/dev/hbd1        ext3             146.18GiB         Boot
/dev/hbd2        entended         2.78GiB
     /dev/hbd5   linux swap       2.78GiB

I don't understand why the problem seems to be intermittent?  Surely the Grub must be either stable on the partition or not!?!?

I was half way to copying files between the XP drive and the Gutsy drive, I don't really want to re-install as am probly gonna lose data.

Any ideas or advice on making the system stable, much appreciated.

TB

---

### Post by Sorivenul on 2007-11-24
Have you tried reinstalling GRUB via the LiveCD?  That may fix your issue.  The link is here:  [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351").  Try it out.  Try it out.  I've had similar issues myself, and this always seems to fix it.

---

### Post by truthbrush on 2007-11-25
Thanks for the tip.....I got the system back up by a similar method.

Touch wood everything has been stable for the past 2 days now and the machine is booting to grub menu everytime.  I'll just keep a tag on it for a while but it's good to have a few different ways to fix things.

---

