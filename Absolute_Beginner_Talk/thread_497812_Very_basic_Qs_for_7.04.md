---
title: "Very basic Qs for 7.04"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by KlondikeGeoff on 2007-07-10
Computer user since 1981, Win (ugh) user since ver 1.0, used very one since except Vista. 

Finally bitten the bullet and downloaded Ubuntu 7.04. However, want to keep Win for a while, certainly, until finished test driving Ubutu.

Have downloaded the latest version and burned a CD. I see there is a wealth of info online, but in a cursory look, see that will probably have to wade through tons of stuff to find some basic facts. I'll study it all later, but need some  questions answered.

First, the CD boots OK, and lists some programs I can try. I don't see anything on the opening screen to install the program permanently. So, that's Q#1, how to install.

Q#2: I understood the CD gave a full working version of Ubuntu, so could try it out before installing, but this does not seem to be the case, it only lets me install Firebox (already use that), Abiword, etc. No way to see if printers and other USB devices work, etc.

Q#3: My XP Home desktop has two separate HDDs, each with two partitions. The first drive, C: & D: has Win and some applications on C: and most everything else on D: The second drive, E: & F: has very little on it, mostly backup stuff.

So, can I install Ubuntu (once somebody tells me how :) ) on the E: drive on the second HDD, or does it have to go on the Window partition? I understand it creates it's own partition, so hate to put it on the C: drive unless absolutely necessary. My second choice would be to install it on the D: partition.

I assume then I would have a dual-boot setup where could pick Win or Ubuntu. Correct?

Any help will be appreciated.

---

### Post by Freddie.Ruddick on 2007-07-10
1/2) Although the Ubuntu CD has some applications for windows use, it can also be used to try/install Ubuntu. What you need to do is boot from the CD. To do this, simply reboot with the CD in the drive. If this does not work, you may need to edit your boot order in the BIOS.

3) Yes, you can resize one of your partitions (E/F), to leave room on the second disk to install Ubuntu. I'm not entirely sure how to do it though.

And yes, you can have a dual-boot, where you are presented with a menu when you boot.

---

### Post by bobplano on 2007-07-10
for questions one and two, you need to boot into your cd. restart your computer and press the button it says right when your computer boots up to enter bios setup. there should be boot order somewhere in there, and then change to boot order so cds boot first. you should be able to then boot off the cd, and install it. ubuntu uses ext3 filesystem so you need to make your own partitions. you need at least two, one is ext3 and mounted to "/" (without the quotes), and the other is swap. read [this]("http://psychocats.net/ubuntu/installing") for a better explanation.

---

### Post by ukripper on 2007-07-10
> **KlondikeGeoff said:**
> Computer user since 1981, Win (ugh) user since ver 1.0, used very one since except Vista. 

Finally bitten the bullet and downloaded Ubuntu 7.04. However, want to keep Win for a while, certainly, until finished test driving Ubutu.

Have downloaded the latest version and burned a CD. I see there is a wealth of info online, but in a cursory look, see that will probably have to wade through tons of stuff to find some basic facts. I'll study it all later, but need some  questions answered.

First, the CD boots OK, and lists some programs I can try. I don't see anything on the opening screen to install the program permanently. So, that's Q#1, how to install.

Q#2: I understood the CD gave a full working version of Ubuntu, so could try it out before installing, but this does not seem to be the case, it only lets me install Firebox (already use that), Abiword, etc. No way to see if printers and other USB devices work, etc.

Q#3: My XP Home desktop has two separate HDDs, each with two partitions. The first drive, C: & D: has Win and some applications on C: and most everything else on D: The second drive, E: & F: has very little on it, mostly backup stuff.

So, can I install Ubuntu (once somebody tells me how :) ) on the E: drive on the second HDD, or does it have to go on the Window partition? I understand it creates it's own partition, so hate to put it on the C: drive unless absolutely necessary. My second choice would be to install it on the D: partition.

I assume then I would have a dual-boot setup where could pick Win or Ubuntu. Correct?

Any help will be appreciated.


A#1 When you boot CD click on First option available it will boot Live CD and from within you can install ubuntu 7.04. Follow A#3

A#2 Live CD will show you the installed Hardware before installing once you boot into it

A#3 Here is little visual Howto for you [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

Yes for Dual boot setup!

---

### Post by KlondikeGeoff on 2007-07-10
OK, guys, thanks for the info. Obviously, I did not reboot the box with the CD in it (DUH). Once I tried that, it opened just fine and played around with things from the CD.

Way cool, I can see I'm going to like this once I install it, get the preferences set, and organize my files. etc. So far everything I've read about it seems to be true, much simpler than I expected.

I'm sure I'll be back with more questions soon. :)

---

### Post by ukripper on 2007-07-11
> **KlondikeGeoff said:**
> OK, guys, thanks for the info. Obviously, I did not reboot the box with the CD in it (DUH). Once I tried that, it opened just fine and played around with things from the CD.

Way cool, I can see I'm going to like this once I install it, get the preferences set, and organize my files. etc. So far everything I've read about it seems to be true, much simpler than I expected.

I'm sure I'll be back with more questions soon. :)

Sure mate, keep us updated with your experience on 7.04. Goodluck

---

### Post by J11Gyro on 2007-07-11
You will like Ubuntu I think, I am in same boat with Windoze. The hardest thing for me to get used to is file extensions and which files I can mess with. Right now dual booting with complete 60gig drive as Ubuntu 7.04. There are so many options you can use and play with it may take awhile but it is easy and fun. Welcome to a great community. Soon all the boxes at the house will be Linux except one :) and that box will be dual boot 98SE for gaming. I will probably build a second for dual boot with XP just cause I can but main OS will be Ubuntu.

---

### Post by hyper_ch on 2007-07-11
A good start for beginners that will answer a lot of question is this website here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

