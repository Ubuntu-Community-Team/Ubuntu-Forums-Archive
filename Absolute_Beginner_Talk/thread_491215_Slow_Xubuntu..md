---
title: "Slow Xubuntu."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by mastersync on 2007-07-03
Hello people, I just succeeded installing Xubuntu and everything is fine. Except that its a little slow for a 500Mhz/128MB Ram laptop.


WinXP runs faster than this. 

Anyway to fasten things up ? 

I also want to know how can I free up space for my 5GB HD.

Thank you!

---

### Post by IainT on 2007-07-03
Those are pretty marginal specs for xubuntu. I run puppylinux on a celeron 433 with 96mb RAM and that can be frustratingly slow.

You could try installing fluxbox or icewm and seeing if that speeds things up a bit.

---

### Post by Rocket2DMn on 2007-07-03
Agreed, I think 128 RAM is below the minimum specs for using Ubuntu (even Xubuntu).  It sounds like you need a lighter distro for this box (see above post).  Another option is to keep your eye out for more RAM, people are always getting rid of computers as old as this, you could probably scrounge up some RAM from somebody's old computer for free, or at least dirt cheap.

PS: for free space, you can uninstall unnecessary programs that come preinstalled, and keep your downloaded packages clean with
```
sudo apt-get autoclean
```
Also, when you uninstall, I think you can use "autoremove" instead of just "remove" to make sure you clean out all extra files and broken dependencies.
Good luck

---

### Post by sad_iq on 2007-07-03
Well it's a slow system...and a (more or less)heavy distro...it runs slow on my system also....Many things can cause this...slow Hdd...unenabled dma, video driver..etc. Here are some links... :
 [http://ubuntuforums.org/showthread.php?t=459101&highlight=speed](http://ubuntuforums.org/showthread.php?t=459101&highlight=speed) (speed up hdd)
[http://ubuntuforums.org/showthread.php?t=189192&highlight=speed](http://ubuntuforums.org/showthread.php?t=189192&highlight=speed) (general speed improvements...a little outdated...but a must read anyway)
[http://ubuntuforums.org/showthread.php?t=107856&highlight=speed](http://ubuntuforums.org/showthread.php?t=107856&highlight=speed) (tweak ext3)

Also could you explain more what is working slow with it(browsing, booting..)???
 And if possible get your hands on puppy linux...and you'll see the difference!!!

---

### Post by mastersync on 2007-07-03
The booting was slow, it took me 2 minutes to get to Xubuntu.

Everything else is good, not too slow only when launching application, it took 5-8 seconds.

Thanks for the link, I will read it!

---

