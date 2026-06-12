---
title: "um, i am on ubuntu right now (partition)"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by isnipe on 2007-06-12
i need help making a partiotion. I need to do it with my exsisting disc that comes  with my mac. i have 140 gb available, and i wanna make a 40gb partition, how?

---

### Post by starcraft.man on 2007-06-12
> **isnipe said:**
> i need help making a partiotion. I need to do it with my exsisting disc that comes  with my mac. i have 140 gb available, and i wanna make a 40gb partition, how?

Ummm, I don't know much about the Mac. But I am pretty sure all recent version of OSX have a built in partitioner and that it is preferable to use that to resize the partition (I assume its a 140 GB internal and its all to OSX, resizing with GParted might cause problems like with Vista). It will automatically move around all your data from everything I see, its very "just works". Then just leave the empty space (40 GB you wanted...) with no format, I don't think it does Ext3... could be wrong.

So ya, just boot into mac and do that. Then go back to the live CD and continue installing. You can just cancel the install now, you haven't modified anything until you confirm the next screen.

Oh and when your back in Ubuntu, [follow this through the Live CD]("http://www.psychocats.net/ubuntu/installing") install I assume your doing.

---

### Post by isnipe on 2007-06-12
actually its a 250 gb internal hard drive. The main reason i want linux is cause i cant gett t ahold of windows, i am sick and tired of playing americas army with 2 fps on a very good comp.

---

### Post by starcraft.man on 2007-06-12
> **isnipe said:**
> actually its a 250 gb internal hard drive. The main reason i want linux is cause i cant gett t ahold of windows, i am sick and tired of playing americas army with 2 fps on a very good comp.

Uh, well honestly..... I don't know if Ubuntu is for you if _only_ wanna game. I mean I can't really recommend an entirely different OS just to play games. Thats up to you, there are plenty of places to Get a free copy of the latest Parallels (supports direct x 9 games in VM now) and Xp... *looks shifty eyed*

If you still wanna install Ubuntu though (or just don't want to pirate), I just checked and [America's Army]("http://appdb.winehq.org/appview.php?iAppId=908") is certified to run with WINE very well it seems, 2.8 a bit troubled but 2.7 is gold.

So follow the guide if thats what you want, can't hurt to try. Maybe you'll even come to like Ubuntu :). It is more than just a gaming platform though.

---

### Post by Calash on 2007-06-12
You will want to boot to your OSX install disk and use the disk partition utility there.  That will make sure your mac partition is not damaged.  You do not want to partition the new space...the ubuntu CD will take care of that.  Just make sure the space is free and not part of your MAC install.

---

### Post by isnipe on 2007-06-12
a while back i tryed limewiring windows and sttuff in iso then burning it. the file didnt work ( ieventually got caught by my isp dl'ing vg's) sso i am done with illegal. but right now i still have that partition cause it was never used and its still there. But when i selcted it to go on to the next step it wont work it says, "no root file system is defined please correct this from the partioning menu now."

---

### Post by starcraft.man on 2007-06-12
> **isnipe said:**
> a while back i tryed limewiring windows and sttuff in iso then burning it. the file didnt work ( ieventually got caught by my isp dl'ing vg's) sso i am done with illegal. but right now i still have that partition cause it was never used and its still there. But when i selcted it to go on to the next step it wont work it says, "no root file system is defined please correct this from the partioning menu now."

That means you didn't partition a root directory (/) for the installation to use. Please read the first link I gave for installing via Live CD. The partitioning section explains what to do... you just want to go back and make a root partition for the entire space likely with a small swap file.

---

