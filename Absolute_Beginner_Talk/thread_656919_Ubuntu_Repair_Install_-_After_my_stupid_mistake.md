---
title: "Ubuntu Repair Install - After my stupid mistake"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by silv3rback on 2008-01-03
Hi guys

I feel like a real no0b posting this, but here it goes....
OK, so yesterday I was playing around with Ubuntu, and was trying to install angry ip scanner, was following a guide of these forums. It said copy the .jar file into /opt dir... I couldnt do that, so after a few attempts I logged into root, and decided to change all the permissions on the folders on the Filesystem, which in turn screwed up my PC. I've tried booting into repair mode (I think thats what its called) but nothing happening...

I cant boot into Ubuntu anymore:( Is there any way to either restore permissions back to default, or do a  repair install with Ubuntu?

---

### Post by forestpixie on 2008-01-03
there's been a few of these lately - the general consensus was to reinstall. There isn't a repair install that I know of and you'd be there for a lot longer trying to repair permissions than it takes to install

---

### Post by carrett on 2008-01-03
Yeah, that's gonna be a bitch...this is why I always make backups! Actually, what I really do is keep /home on a separate partition. Installation is so easy these days that I'd only really be screwed if all my files and prefs were lost (but system-wide stuff is easily replaced, for me anyway).

---

### Post by silv3rback on 2008-01-03
I dont have a problem with losing any files, they all on a seperate hdd, I just wanted to see if I could keep my settings. Im definately learning, but the hard way....

I think I'll just have to clean install when I get home

---

### Post by forestpixie on 2008-01-03
I know that feeling - learn't quite quickly how to get a new install back to how I like it

---

### Post by silv3rback on 2008-01-03
lol!!

Its happened to me a few times now.... And after each clean install it takes me a few minutes less to get things back to how they where

Im dual booting XP with Ubuntu, I only use XP for gaming.... the rest is all on Linux, Im loving it:) Thanks for the replies guys

---

### Post by Perfect Storm on 2008-01-03
...and the lesson is; don't mess with the permission of root :KS

---

### Post by silv3rback on 2008-01-03
> **Artificial Intelligence said:**
> ...and the lesson is; don't mess with the permission of root :KS

Lesson learnt:):lolflag:

Clean install here I come

---

### Post by hyper_ch on 2008-01-03
you could try to no select the "format partition" option upon manual partitioning... I assume it will then just overwrite existing configurations files - however I've never done that before!

**BACKUPS ARE GOOD... BACKUPS NEED TO BE DONE ON A REGULAR BASE!**

---

### Post by argie on 2008-01-03
> **silv3rback said:**
> I dont have a problem with losing any files, they all on a seperate hdd, I just wanted to see if I could keep my settings. Im definately learning, but the hard way....

I think I'll just have to clean install when I get home

Woah, hold on. You just have to boot into your LiveCD and copy your /home folder onto another partition to save all your personal settings. To save system wide settings, you just have to copy out the /etc/ directory. Even if you've screwed up your installation, you will still have access to your other settings which you can just restore one-by-one as and when you find you need them.

Then reinstall. If by keeping files on another hard-drive you meant that your /home partition was on another hard drive then it's all cool.

---

### Post by silv3rback on 2008-01-03
Lemme get this straight..... If I copy the /etc dir, and then clean install, I'll still have all my settings when I copy the foler back?

I dont have any files or folders on the same partition on my Linux install, I keep it on a seperate drive
Also, I was thinking, cant I boot into the Live CD, and restore the default permissions somehow?

---

### Post by hyper_ch on 2008-01-03
no, the personal settings are in your /home folder... the /etc folder contains system-wide configuration settings. So you'd need to backup /home and /etc... however with just moving then those config files back, will not install the software you. Additional software you installed you'll still need to install.

---

### Post by silv3rback on 2008-01-03
Meh..... I think a clean install would work better anyway:)

Thanks for all the advise guys, much appreciated

---

### Post by markyb86 on 2008-01-03
how do you go about having a seperate /home partition? i need to get me some of that!

---

### Post by silv3rback on 2008-01-03
> **markyb86 said:**
> how do you go about having a seperate /home partition? i need to get me some of that!

I dont think I explained myself very well a few posts ago... My Home folder is on the Linux parition, but all my files - mp3's, movies etc etc is on a different HDD


Im sure you can find some way to do it though on here, theres everything on these forums!!:popcorn:

---

### Post by argie on 2008-01-03
> **markyb86 said:**
> how do you go about having a seperate /home partition? i need to get me some of that!
Well, if you've already been using Ubuntu without a separate /home partition, here's a good tutorial:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you haven't installed yet or don't mind reinstalling, when the partitioner starts in the Install screen, choose manual partitioning and create two different partitions, one with mount point / and one with mount point /home. You can choose any size you want, just don't make it very tiny or you may have trouble later on (a few MB is 'really tiny').

---

