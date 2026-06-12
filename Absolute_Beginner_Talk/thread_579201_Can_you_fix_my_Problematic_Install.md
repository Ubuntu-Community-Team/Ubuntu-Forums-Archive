---
title: "Can you fix my Problematic Install?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dwilson08 on 2007-10-18
Okay today I decided to install Ubuntu (Why I couldn't wait a few hours until 7.10 I don't know) For whatever reason I decided the release candidate was good for me (Obviously because I've used Ubuntu for about 5 days in my life before now) and the Installation went alright. I tried to enable desktop effects (I like eye-candy okay?) and I couldn't get it to work. I then assumed perhaps I needed some kinda nVidia driver because my laptop has some kinda nVidia card. Easier said than done. I ended up screwing up my xserver sometihng... and screwed up xorg.conf (perfect) Then ubuntu hung on the boot. I'd have to go into command line during bootup... and undo changes with xorg (god know's how I pulled that off) then using the command startx (I don't remember where I found that) I got it to start. Yay. But not actually. Things were still screwed. I decided to back out of ubuntu so I did the only logical thing. Deleted my linux partitions from windows. Then when I tried to boot into windows GRUB went "WTF?" I don't have a windows CD around anywhere to fix that... so I installed Ubuntu again (hey, why not) so GRUB would work. Now here I am on my new install... and it's seriously screwed. I can't install packages via "Add/Remove Applications" because apparently nothing can be installed on a i386 type computer (WTF?) Now that 7.10 is available... is there anyway I fix all my problems? Formatting my hard drive isn't an option (I don't have a vista CD) If I delete my partitions again... and use the 7.10 CD will it be any better. Please note: If you couldn't figure it out from this novel.... I'm a bit linux-retarded.
Thanks in advance.

I'm using hp9500 laptop with Intel core2duo (1.66 GHz) with some kinda nVidia integrated graphics... 1gig ram...and other such niceties.

---

### Post by dwilson08 on 2007-10-18
I should summarize that.

I installed RC1.
No desktop effects.
I screwed up ubuntu
I deleted ubuntu
I installed ubuntu
ubuntu is screwed up

How can I completely re-install Ubuntu?

---

### Post by slira on 2007-10-18
Hi
it happened to me once...
You can use the partitioner in the live CD to start from scratch - (never worked for me really good)
or you can "clean" your linux partitions from vista using a partition manager (really get rid of them and create non-allocated space in your hdd)
then, reinstall ubuntu from the beginning using the live cd
using the live cd create a root partition and a swap partition (swap should be 1,5x your ram)
(you might also create a /home partition to easy things after; it would be your "documents" partition. but it should be logical, under root, ok?)
my installations worked better when I did the partition tasks "by hand", not using automatic during live cd installation.

(linux changed your MBR, that's the reason your vista is not booting)

good luck! have fun - it will finally work, do not worry :)
best
slira

---

### Post by mikeyphi on 2007-10-18
> **dwilson08 said:**
> I should summarize that.

How can I completely re-install Ubuntu?

Boot from the LiveCD
select 'Install'
Take the guided or manual partition option
select the previous Ubuntu partitions - be careful!
following installation - go to 'System/Administration/Software sources' and enable the repositories.
enable wireless card - if needed
select Restricted Driver Manager - this will prompt for driver download - go ahead.
Following a restart your system should be up and running.

If you used the RC LiveCD there will be some package updates.
By all means use Terminal commands to alter the basics - if you wish - but there are many good GUIs now available, by default, to help users set up their individual system.

---

