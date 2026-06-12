---
title: "lappy doesn't like linux?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by pointmeatthesky on 2007-02-05
I got a new laptop on Friday. Here are the specs:

HP Pavilion dv6000
2.0GHz AMD Turion 64 X2
1 GB RAM
160 GB hard drive
nVidia graphic card (I'm not positive on the exact model, but I'm pretty sure it was 256mb and the best that HP offered)

So here's what I've been doing the last few days..

I have three Ubuntu CDs. One 32-bit 6.06, one 64-bit 6.06 Kubuntu, and one 32-bit 6.10 Kubuntu (this is the only downloaded one). At first, none of them would boot at all. I think I got the 6.10 Kubuntu and the 32-bit 6.06 Ubuntu to boot once. Each time, they froze during the install. Every other time I tried, they wouldn't boot whatsoever. During the boot up, though, each disc had the same "bcm43xx_microcode5.fw" error, but by Googling, I found out that that has to do with the wireless card.

After that, I downloaded Ultimate Ubuntu and couldn't get that to boot either. Then I found out about the md5sum checker. Apparently, the Ultimate Ubuntu md5sum didn't match.

Then I tried downloading OpenSuSE 10.2 and Sabayon 3.26 and those md5sums didn't match.

Anyone know what the problem could be? Am I stuck with Windows? I just ordered an OpenSuSE 10.2 disc. Hopefully that'll work.

---

### Post by shareMenaPeace on 2007-02-05
Make sure you burn the ISO files on slowest speed(x4) and verify the data.

---

### Post by Zuuswa on 2007-02-05
Most of the Ubuntu distributions have alternate installation cds.  You should try those, and make sure the md5sums match!!  There is a windows installer in the form of an .exe, but I have not tried it and it is only in beta stages and it sounds like it is rather buggy.  Use at your own risk [here.]("http://ubuntuforums.org/showthread.php?t=338279")

---

### Post by pointmeatthesky on 2007-02-05
My main problem with downloading Linux is that the md5sums never matched.  Any idea why, or how I could fix it?  I've tried mirrors and bittorrent and neither seem to work for me.

---

### Post by shareMenaPeace on 2007-02-05
This might be handy

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by pointmeatthesky on 2007-02-05
> **shareMenaPeace said:**
> This might be handy

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Tried it.  I have a Ubuntu and Kubuntu disc and neither would boot up right.  Well, I got the Ubuntu one to boot up once, but it froze during install.

---

### Post by irish_flu on 2007-02-05
That's really weird, I have no idea why you're having such problems booting.  It sounds like burn problems (or download problems), since the md5sums don't match.

Sounds like really darn nice laptop, though; I hope it works out with one distro or another.

I agree with others that you might try getting the "alternate" CD....

---

### Post by pointmeatthesky on 2007-02-05
How do the alternate install discs work?  They're not graphical, are they?  Can you still dual boot with them?

---

### Post by TrIde2188 on 2007-02-05
I have had to revert to using alternate cd's as my laptop is well to put it simply a pile of cr*p :]


Its basically THE basics of ubuntu where as the normal cd i think comes with loadsss of extra packages etc etc.

---

### Post by shareMenaPeace on 2007-02-05
Here is a burning howto
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And try the 6.06 32bit release again.

---

### Post by pointmeatthesky on 2007-02-05
> **shareMenaPeace said:**
> Here is a burning howto
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And try the 6.06 32bit release again.

That's exactly how I did Kubuntu 6.10, and I could only get it to boot once or twice.

My 32-bit version of Ubuntu 6.06 is a ShipIt disc, so I figured that would work over everything else.

But if my OpenSuSE disc doesn't work for me, I'll try downloading 6.06.

---

### Post by empthollow on 2007-02-05
try this site, this is a place where people post which distros and how well they work on specific laptops. Even if it doesn't have yours specifically you can find some good info on similar models. [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by teaker1s on 2007-03-03
I have the DV6116eu and it got so bad I'm moving it to debian etch, edgy had kernel issues and feisty has xorg issues and beta nvidia driver wouldn't install. I also started a wiki page on DV6000 pm me if you'd like more info

---

