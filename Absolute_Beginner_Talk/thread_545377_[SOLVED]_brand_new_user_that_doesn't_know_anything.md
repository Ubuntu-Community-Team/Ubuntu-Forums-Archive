---
title: "[SOLVED] brand new user that doesn't know anything"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by bigpenguin on 2007-09-07
I just installed feisty fawn on a compaq laptop dual-booting with xp.  I installed after some trouble so I had to use the alternate cd.  I think I saw a thread about ATI X*** vid cards so I think that is the problem that I was having.  Anyway, I have it installed now but I am having trouble with my wireless card.  I should say that I am completely new to Linux and not overly confident with coding and all that jazz so talk to me like I am a complete idiot.  During the install I skipped over the internet stuff because I didn't have the WEP info on hand.  Now I am trying to get on the internet and I can't.  I don't know if my wireless card isn't supported and I need NDISwrapper or something, or if I am just dumb and can't configure my network card correctly.

Any help would be appreciated and I am sure this is an easy one for you guys :)

Thanks,

Tim

---

### Post by LaRoza on 2007-09-07
> **bigpenguin said:**
>  I don't know if my wireless card isn't supported and I need NDISwrapper or something, or if I am just dumb and can't configure my network card correctly.

Any help would be appreciated and I am sure this is an easy one for you guys :)



Giving the exact card you have will get you some help.

Welcome to the forums, and I hope you find this community helpful!

---

### Post by bigpenguin on 2007-09-07
yeah, sorry, that was dumb.  It is a Broadcom 802.11a/b/g WLAN.  

On the NDISwrapper site I saw all sorts of other info like "BCM4310 UART" or "AirForce One" for Broadcom cards, but I don't see anything like that for my card.

If you need to know more than that maybe you could help me find it.

Thanks

---

### Post by daveshields on 2007-09-07
BigPenguin,

You already do know something -- Ubuntu has the largest, most friendly and most helpful community  yet seen that has gathered together to support a Linux distribution.

---

### Post by SpiritIsReality on 2007-09-07
howdy

for ndiswrapper , success started here for me.
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)

I think the command lspci gives you an idea of your card, if it's recognized by the kernel.
good place to have a look at commands
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
some laptops/notepads have a place to plug in a cable to your network, works til you get your wireless going.
this
[http://ohioloco.ubuntuforums.org/showthread.php?t=405990](http://ohioloco.ubuntuforums.org/showthread.php?t=405990)
was recommended here
[http://ubuntuforums.org/showthread.php?t=545221](http://ubuntuforums.org/showthread.php?t=545221)


trails

---

### Post by P235 on 2007-09-07
Here's another thread that may help:

[http://ubuntuforums.org/showthread.php?t=361917&highlight=restart+internet](http://ubuntuforums.org/showthread.php?t=361917&highlight=restart+internet)

---

### Post by SpiritIsReality on 2007-09-07
P235 ...thanks for the links
quote from P235 at this thread
[http://ubuntuforums.org/showthread.php?t=545221](http://ubuntuforums.org/showthread.php?t=545221)

"I do not know which guides you've read, but I suggest you read these two as well:

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) [For downloading and installing ndiswrapper via make]

[http://ubuntuforums.org/showthread.php?t=361917](http://ubuntuforums.org/showthread.php?t=361917) [Installing ndiswrapper w/ repos]

The basics can be found in these two treads and they've helped me get my wireless card working. For threads that address particular cards, visit:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) "

trails

---

