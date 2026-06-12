---
title: "New Installation...Cannot Boot"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by SpudDogg on 2005-09-16
I just installed Ubuntu, and the installation went smooth.  After it asked me to take the disc out and restart, the computer will not boot at all.

I get to the screen where it says "ubuntu" and has the logo and the progress bar.  At about 50%, the computer freezes solid.  By "solid" I mean when I press caps lock or numlock, lights on the keyboard don't even turn on/off.

When I boot in "Recovery Mode", loading runs then freezes with the message "[4294691.688000]   <0>Kernel panic - not syncing: Attempted to kill init!

Anyone know what that means?

Any help would be greatly appreciated.  Thanks!

---

### Post by aysiu on 2005-09-16
I don't know much about how to fix problems like this, but I do know the last time I had kernel panic, it was because the Grub menu.lst entry was messed up. Since it was a fresh install, I doubt that's the problem.

I've always found something like [this search](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=Kernel+panic+site%3Aubuntuforums.org&btnG=Search) to be helpful in diagnosing problems like this.

---

### Post by SpudDogg on 2005-09-17
Ok, thanks.  I looked around those for a while, and it seems as though everyone there is trying to update, which is not my case.  Remember, this is happening before I can even load Ubuntu!

Anyone else have any ideas?

---

### Post by blastus on 2005-09-17
It may be just a botched installation. The first time I ever installed Ubuntu it wouldn't load X (the Windowing system.) For some reason, the installation just did not work properly. However, subsequent installations of Ubuntu worked fine even though I just pressed enter to install and didn't do anything differently. Over the years I've had a couple of botched installations with MS-Windows also. It's a pretty rare occurrence I think, but it can happen.

---

### Post by SpudDogg on 2005-09-17
Ok...my problem is solved.  All I did was remove all unneeded hardware (in this case video card and modem), and everything works great!

Thanks for all the help!

---

