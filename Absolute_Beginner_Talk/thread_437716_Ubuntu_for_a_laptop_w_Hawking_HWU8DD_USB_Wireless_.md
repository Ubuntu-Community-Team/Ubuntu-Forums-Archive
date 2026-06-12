---
title: "Ubuntu for a laptop w/ Hawking HWU8DD USB Wireless Dish"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by trinaryouroboros on 2007-05-09
Hey, I've been toying with Ubuntu since Hoary Hedgehog, primarily endeavoring to fight the facets of 64-bit (which is mad easy now!) - and am finally considering using it on my little laptop.

However, I have a Hawking HWU8DD Wireless USB Dish I've been using to get signal wherever, and was hoping someone could shed light on whether or not it's _truly_ compatible/usable with Ubuntu Feisty Fawn (got the new CD's, killer)

I ask primarily because I NEVER used any of the WiFi stuff in Ubuntu as I've only really stuck to installing it on Desktops thus far...and, in the past there were odd nightmares I'd randomly run across concerning WiFi adapters and Ubuntu (which *Appear *to have been since corrected...)

The HWU8DD Dish is also fairly new stuff, and Hawking Technologies made a beautiful mess up already by giving the crumby non-usable drivers on the CD that comes with it ... so I'm sort of anticipating similar trouble concerning Ubuntu.

Any advice/stuff is greatly appreciated, I wish I could find something on the web that states it's compatible/etc., but, the only thing I've found is some drivers for a mobile OS called Slax [shrug]

---

### Post by prabbit237 on 2007-05-09
Not even heard of that particular wireless device but if you can get drivers for it that work for windows XP, you can probably use ndiswrapper in Ubuntu with those same drivers.

There's loads of places for how to install ndiswrapper (just google the words "ndiswapper ubuntu howto" without the quote marks.)

---

### Post by trinaryouroboros on 2007-05-09
Okay, will do, i'll give it a shot today and go gung ho on the install.

---

### Post by trinaryouroboros on 2007-05-09
Bah, I'm having second thoughts already. I don't see the Hawking on either native or ndiswrapper supported lists:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsHawking](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsHawking)

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

I s'pose I could still try it out and pray.

Also learned HWU8DD seems to use the zd1211 linux driver files, I have those handy to play with now.

---

### Post by hamster_billy on 2007-10-18
In case anyone's still watching this thread, this is on the maplin.co.uk website:
> 
Q) Not a question just feed back: Works as soon as it''s plugged in to Ubuntu 7.04
A)thank you very much for the feedback

---

### Post by trinaryouroboros on 2007-10-18
Oh...guess I should install that, or something.

:lolflag:

---

### Post by Shin2010 on 2008-02-27
I'm in the same boat as you are with this HWU8DD, but after reading this thread found a site that works for it. [http://www.linuxwireless.org/en/users/Download](http://www.linuxwireless.org/en/users/Download) But just have to add in some odd things,
when using this if your using a laptop this driver disables any other wireless drivers so I am guessing duck tape the dish on the back of the screen, the other thing if you unplug it and plug it back it will not work until you restart the computer with it plugged in. But other then that it works pretty good.

GOOD LUCK!

:lolflag:

---

