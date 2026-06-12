---
title: "Conflict???? Help please!!!"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by allinga2259 on 2007-04-03
Have spent days trying to boot Ubuntu from live CD ( APC mag- aug 06 issue) - I get the first screen and slect install, it appears tp load and I then get a black screen with - 'Uncompressing Linux ... OK, Booting kernel ' next line has a cusor then I get nothing.
Today I decided to take a risk and try it on our home office computer and away it went??? 
The computer it wont boot on is - 
Asus P5W M/b
2gd ram
Winfast px7600gt
winxp on sata hdd - ntfs
separate 80gd ide hdd - fat32 (none of which should have any bearing on it because the live cd only uses ram.

Any ideas please?????

---

### Post by johnny4north on 2007-04-03
which ver of ubuntu are you try to boot w/?  im useing ubuntu 7.04 beta, but final release is on the 19th.  i would wait till then.:)   24000 seconds til then...

---

### Post by jvc26 on 2007-04-03
Have you tried to run the check disk option? This will check if there are any errors on the cd as you may have a faulty cd.
Il

---

### Post by jhenager on 2007-04-03
I have read that Linux support from Asus is less than desirable, at least from one person's report on the web.
[http://mozillaquest.com/Linux04/Asus_Sucks_Story-01.html](http://mozillaquest.com/Linux04/Asus_Sucks_Story-01.html)
However, since then, I see that Asus is working to try to provide better support, and even includes a support CD with Linux drivers.
[http://event.asus.com/intel/](http://event.asus.com/intel/)

The first thing I would check is your motherboard model to see if it is one that is known to be Linux friendly.


Edit: found some other people using the P5W, and it looks like that might be where the problem lies.
[http://bbs.archlinux.org/viewtopic.php?pid=239715](http://bbs.archlinux.org/viewtopic.php?pid=239715)
<quote> I so hope this will work, i've wanted to use Arch for over 8 months since i got my new motherboard.. (asus p5w dh deluxe) and had no luck with any linux distros apart from gentoo (which is tedious) </quote>
<quote> There are some issues with the linux kernel and the P5W.</quote>

---

### Post by chili555 on 2007-04-03
This is a known bug: [https://launchpad.net/ubuntu/+bug/58358](https://launchpad.net/ubuntu/+bug/58358) I believe in later kernels, 2.6.20-x, it may be fixed. You might try downloading, burning to CD and booting from the latest beta version, Feisty. [http://cdimage.ubuntu.com/releases/feisty/herd-5/](http://cdimage.ubuntu.com/releases/feisty/herd-5/)

---

### Post by allinga2259 on 2007-04-03
Many thanks to those who replied. After heaps of reading the various links I realise and appreciate the amount of work that goes into fixing these bugs. I really want to start using linux instead of that 'other OS', but will wait until the 19th. 
Thanks again, all.:KS

---

