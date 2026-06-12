---
title: "[SOLVED] how do I back up an install I like?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-01-05
I've been using Gutsy for a couple of months now, which means all the stuff I like is installed, updates are up-to-date, etc. Is there a way I can copy this install to put it as it is on another computer so I don't have to do the whole thing again?

---

### Post by shanepardue on 2008-01-05
You can image the partition (Like Norton Ghost for Windows). There's a pretty cool program called [Partimage]("http://www.partimage.org/") that can do this very effectively.

---

### Post by thelatinist on 2008-01-05
> **shanepardue said:**
> You can image the partition (Like Norton Ghost for Windows). There's a pretty cool program called [Partimage]("http://www.partimage.org/") that can do this very effectively.

This is a good option, but **only** if both computers have the same hardware.  If they differ, there will probably be problems (hard disk mounting, video drivers, etc.).  It may be more work editing fstab and restoring grub and playing with drivers.

I believe there is a way at least to duplicate the installed software by using Synaptic to generate a shell script that will download and install all your installed packages.  I've never done it, though.

---

### Post by sergiom99 on 2008-01-05
Hi. If I run something like "Hiren's boot CD" and try to make an image out of my ext3 partition, would it work if I just try to restore it at a later time? Lets say I used Ghost or something similar.
Thanks.

---

### Post by Yoke &amp; Chung on 2008-01-05
> **sergiom99 said:**
> Hi. If I run something like "Hiren's boot CD" and try to make an image out of my ext3 partition, would it work if I just try to restore it at a later time? Lets say I used Ghost or something similar.
Thanks.

If you restore the image back to the same PC? It should work. I have done it many times with Partimage and Clonezilla.

---

### Post by sergiom99 on 2008-01-05
> **Yoke & Chung said:**
> If you restore the image back to the same PC? It should work. I have done it many times with Partimage and Clonezilla.

Thanks. Yes, in the same laptop. I plan to make a backup of my working install since it took quite a bit to get it running.
With partimage, do you need to format your partition first? I have an NTFS/XP partition and the main ext3/Kubuntu.

---

### Post by thelatinist on 2008-01-05
> Is there a way I can copy this install to put it as it is on another computer so I don't have to do the whole thing again?

I think the original poster is asking how to duplicate his installation on a different computer.  Am I wrong?

---

### Post by kleo skywalker on 2008-01-05
thelatinist, you're right. I want to duplicate my installation on a different computer (with different hardware).
Technically, I do not own the computer I use now. I installed Gutsy though, and everything else on it - it's in a good state, not one I'd want to regress from. So when I get a new (or used) computer of my own, I'd rather start from here as against a basic install.

---

### Post by kleo skywalker on 2008-01-22
While looking for options I came across [this thread]("http://ubuntuforums.org/showthread.php?t=621673&page=2"), where I found [this]("http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html").

So I did pretty much what it says on that link. Graphically, that would be System-->Administration-->Software Sources-->Third Party Software-->Add > deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo/ and updated the repos when prompted, or you could run ```
sudo apt-get update
```
Then System-->Administration-->Synaptic, search for and install remastersys.
Then followed the instructions on that page on how to use remastersys, and opted for dist. It was really easy and created a custom iso of my current Gutsy install which I burnt on to a DVD.
The LiveDVD boots alright though I haven't needed to install it yet.
Also, I don't know if it'll work on different systems but at least I have my install backed up for now.

---

### Post by Born-Thirsty on 2008-01-22
Another option to look at is possibly APT-on-CD, Using this, a user can load all the .deb packages that they have downloaded/installed onto a CD. They can then later use this CD to load all those apps again and the bonus is you do not need an internet connection because you use your CD as the repository.

---

### Post by billgoldberg on 2008-01-22
Another thing you could do is make a copy of you system and convert it to a live cd.

Thus you have your own ubuntu gutsy (fesity) live cd with all your updates/programs you want and you can install that on any pc you want.

Thus reinstalling ubuntu is done with everything you want already installed.

Look [here]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys") for that.

Or take a look at this back-up utility:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462)

---

### Post by philinux on 2008-01-22
According to the site. [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

> Remastersys is a tool that can be used to do 2 things with an existing Klikit or Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.


It says it can be used anywhere.

---

### Post by kleo skywalker on 2008-01-22
> **billgoldberg said:**
> Another thing you could do is make a copy of you system and convert it to a live cd.

Thus you have your own ubuntu gutsy (fesity) live cd with all your updates/programs you want and you can install that on any pc you want.

Thus reinstalling ubuntu is done with everything you want already installed.

Look [here]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys") for that.

That's what I did. I'd looked at the other link too, but this just seemed really easy.

---

### Post by jryprt on 2008-02-08
Remastersys  works , but I had to use DVD-R  , tried DVD-RW did not boot

---

