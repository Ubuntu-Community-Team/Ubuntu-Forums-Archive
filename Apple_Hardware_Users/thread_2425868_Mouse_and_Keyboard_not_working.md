---
title: "Mouse and Keyboard not working"
date: 2019-09-01
forum: Apple Hardware Users
---

### Post by lorn1975 on 2019-09-01
Hello I just installed the Ubuntu 18.04.3-desktop-amd64.iso onto USB drive and booted into Ubuntu on Macbook 2017 laptop but no keyboard and mousepad of the laptop do not work is it a right distribution to use on Macbook 2017 laptop?Thx

---

### Post by wildmanne39 on 2019-09-01
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by bubba9999 on 2019-11-24
Hi - realize this thread is several months old, but did you ever get an answer to your question - or solve it yourself? 

I have the identical configuration (2017 Macbook Pro w/ Touch Bar) running Mojave 10.14.6, but when I boot Kubuntu from a boot stick, the keyboard and mouse (trackpad) are not responsive. Looking on this forum, it appears that many - trying to get one version or another of Ubuntu running on MODERN Mac hardware have exactly the same problem.  I found a thread on apple.stackexchange from several years ago that essentially said that all variants of Ubuntu were NOT well supported on MODERN Mac hardware (and implied that the Ubuntu development community needed to get off their butt and do something about it), but I can't find anywhere were this issue is being pursued. I tried searching the Ubuntu bug database for related issues but found nothing.

So... since the Ubuntu folks continue to advertise that their very pretty OS can replace or run along side of OSX (i.e., on Mac hardware) - one would naturally assume this statement extends to MODERN Mac hardware.

Could someone from the Ubuntu development community take a moment to indicate whether or not ANY version of Ubuntu is functional on MODERN Macbook hardware - say all Macbooks from 2017 to present? And obviously I'm talking about native hardware support: I've read in several places where the "solution" is to get some kind of external keyboard and mouse to operate Ubuntu on your Macbook. Yeah, right - that's what I want to do for a laptop.

Thanks.

---

### Post by oldfred on 2019-11-24
This mentions keyboard issues.
[https://nixaid.com/linux-on-macbookpro/](https://nixaid.com/linux-on-macbookpro/)

I recently saw this, so you may want newest kernel:
As a last minute surprise for the Linux 5.3 kernel merge window is support for the keyboard and trackpads on newer Apple MacBooks and MacBook Pro laptops.

With An Out-Of-Tree Kernel Patch You Can Finally Read/Write To The SSDs On Newer Macs - 2019 July
[https://www.phoronix.com/scan.php?page=news_item&px=MacBook-Finally-Linux-SSD-RW](https://www.phoronix.com/scan.php?page=news_item&px=MacBook-Finally-Linux-SSD-RW)

---

### Post by bubba9999 on 2019-11-25
Thanks for the info.  Let's hope those links are NOT how the Ubuntu folks define 'progress' - those just give me a headache.

However, this does appear to be:

[COLOR=#000000]As a last minute surprise for the Linux 5.3 kernel merge window is support for the keyboard and trackpads on newer Apple MacBooks and MacBook Pro laptops.

[/COLOR]19.10 uses the 5.3 kernel, so when I "try Ubuntu" with a 19.10 boot stick, lo and behold we have a working keyboard and trackpad. Furthermore, wifi and bluetooth work, and my display seems to be behaving as well.  So definitely progress.

However, a few (big) things that don't work: audio output (didn't test input), keyboard lighting, and the really big one: the touch bar.  And you might think, hey, who cares if the touch bar doesn't work, until you realize that all new Macs w/ a touch bar don't have an Escape key - the Esc key is IN the touch bar.  Gotta have at least limited touch bar functionality.

One of the (other) big issues is the mismatch between available documentation/articles, age of the Linux/Ubuntu OS, and age of the Macbook.  Many of the articles on how to do this from say, just three years ago, won't apply to modern Mac hardware, nor will they incorporate changes to Ubuntu over the past few years.  They often create more confusion than answers.  

Anyway, thanks again. Progress - but not quite ready for prime time.

[COLOR=#000000]

[/COLOR]

---

