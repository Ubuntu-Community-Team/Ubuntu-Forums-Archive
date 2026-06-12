---
title: "Upgrading."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-10-14
i'm slightly concerned about when its times to upgrade to the next version of Ubuntu & Kubuntu.

Will there be a way to upgrade straight from Breezy Badger (6.06), to the next, & Kubuntu, or will we need to wipe Ubuntu, loose everything, and re-install completely.

---

### Post by aysiu on 2006-10-14
Breezy Badger is 5.10

Dapper Drake is 6.06

Edgy Eft (coming out in a few weeks) is 6.10

If you have Breezy Badger, I highly recommend you just do a clean reinstall of Edgy Eft or just upgrade to Dapper Drake.

There is a way to upgrade... there are several ways, actually, and you do not need to lose everything. Still, in the past, some people have experienced problems during upgrades (broken X servers, locale issues, etc.). They can be solved, but sometimes people like to reinstall anyway, just to see what the installation is like.

One way involves manually editing your sources.list. Another way is just an automatic pop-up that you click. The automatic pop-up way had mixed results when it upgraded from Breezy to Dapper, but maybe they've refined the process a bit for a Dapper-to-Edgy transition.

Nevertheless, if you reinstall completely, you don't need to lose everything. You can make a separate /home partition and keep all your settings and files:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Captain Kirk76 on 2006-10-14
My mistake, i have Dapper Drake (6.06)

I was just worried i would loose all my customization u had in Ubuntu & Kubuntu.

by the way, when is Kubuntu upgraded?

---

### Post by ewl1217 on 2006-10-14
Kubuntu (as well as Xubuntu and Edubuntu) follows the same release schedule as Ubuntu, so, barring some odd and unexpected event, it shuold all be released at the same time.

---

### Post by thelinux_guy on 2006-10-14
I was wondering about this,It would be nice to see a "settings transfer wizard" in Ubuntu,Because I would hate to lose everything and have to start all over again:-k

---

### Post by NewRubberSoul on 2006-10-14
I know that it's kind of a pain to spend extra cash, but I bought a 250GB external hard drive and it's been worth it.  Not only does it let you back up your information (which is important if *all*  of your pictures/videos/etc. are stored on your hard drive, but it also gives you a lot of flexibility if you ever want to change your OS.  I quit XP, went to Suse, then to Ubuntu and each transition was really easy because I didn't have to worry about losing my files.

The only thing is that you don't retain all of the customization that you did, which would definitely be nice.

It's worth considering, anyway. :-k   All the best with upgrading.  I'm definitely looking forward to October 26th!

---

### Post by catlett on 2006-10-14
The update manager can upgrade your system for you. It is designed to keep all your settings and customizations. The problem is it didn't work very well during the last upgrade. I personally lost everything. From my x server on down. I had to do a clean install from a dapper CD to move from breezy to dapper.
From that experience I learned to use a home partition. Your home partition is the partition that holds all your customization files. They are hidden in your home folder (press ctrl h when you are in your home folder and you will see all the folders). This way I can upgrade from an edgy installation CD. All I have to do is leave my home partition un-formatted.
I have dapper on 2 computers so I'll experiment with the update manager to see how it works this time but I wouldn't use the update manager on my main computer.

---

### Post by aysiu on 2006-10-14
> **thelinux_guy said:**
> I was wondering about this,It would be nice to see a "settings transfer wizard" in Ubuntu,Because I would hate to lose everything and have to start all over again:-k
It's called creating a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

