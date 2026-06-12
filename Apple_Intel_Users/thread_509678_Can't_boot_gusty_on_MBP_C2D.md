---
title: "Can't boot gusty on MBP C2D"
date: 2007-07-25
forum: Apple Intel Users
---

### Post by russo.mic on 2007-07-25
So,  I'm trying to install gusty on my MBP C2D 15 inch, and i'm unable to boot live into it.  

It tells me that I can't load X, which I expect, then it flashes back to a screen and the last thing it says is running local boot scripts  [ok]. and just freezes there forever.  when I hit the power button, it starts running it's shutdown scripts normally.  any ideas?

I can boot Feisty 386 just fine, but not the 64 bit version.  the same thing happens.  And the same thing happens on both versions of gusty.  Any ideas?

Thanks!

Russo

---

### Post by cyberdork33 on 2007-07-25
hit enter or something to activate the console.

you can also switch to another console ( ALT+Fx, where x is 2-6)

once you get a prompt, you should be able to run 'startx' to get xorg running. At least that's the only way I could get it to work on my machine.

I would be careful with gutsy on the Mac, the partitioner is known to be a little funny.

---

### Post by russo.mic on 2007-07-25
Wow,  I should have thought of that.  

Enter doesn't do anything, but I should have thought to switch to a different console.  

I'll try it tonight and report back.
Thanks!

Russo

---

### Post by russo.mic on 2007-07-25
Just reporting back from my Gusty install.  Switching terminals worked fine.  

On the the conquest of wireless support!

Russo

---

### Post by ronocdh on 2007-07-26
> **russo.mic said:**
> Just reporting back from my Gusty install.  Switching terminals worked fine.  

On the the conquest of wireless support!

Russo
Glad it worked. Interested to hear of your results with MadWifi on Gutsy... due to frustration, I've just decided to stick with ndiswrapper on Feisty. =/

---

### Post by russo.mic on 2007-07-29
Ronocdh,  

Madwifi worked fine on my 64 bit gusty.  Compiled pretty much first try.  

Having problems?  I tried NDISWrapper first, out of habit, and I couldn't get it to work strangely enough.  which NDISWrapper version are you using?  

Russo

---

### Post by ronocdh on 2007-07-29
> **russo.mic said:**
> Ronocdh,  

Madwifi worked fine on my 64 bit gusty.  Compiled pretty much first try.  

Having problems?  I tried NDISWrapper first, out of habit, and I couldn't get it to work strangely enough.  which NDISWrapper version are you using?  

Russo
I'm back on 32-bit for a couple weeks as I help newbies I know ease into Ubuntu. Ndiswrapper I know did not work in 64-bit, but I do recall getting it months ago on a 64-bit install. I thought it was as simple as a different version. I'll try that on next install, thank you!

---

