---
title: "Where to report installation issues and is it worth it?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by jon419 on 2006-11-18
Ok, first off, I love Ubuntu.  I got myself hooked with Ubuntu 6.06 a few months ago and today I tried to upgrade to 6.10 using the Live CD.  I had a few issues and I would like to know where to report them, or if it is even worth it.

[SIZE="4"]**Video Card Issue**[/SIZE]

I have an ATI x800xl video card.  When the live cd starts to load, I get that pretty little splash screen but then it just freezes.  The loading bar stops and nothing happens.  I learned that I could turn off the splash screen with the "nosplash" boot option.

So, I turned off the splash screen and it booted up just fine, except X couldn't start because of some problems.  Here is the problem.  Ubuntu was nice enough to detect my video card, but the driver they used was "ATI".  This gave me an error like:
```

(WW)
ATI:PCI
mach64 5:0:1
in slot 5:0:0 
could not be detected

```

I had to change the driver to VESA so I could boot up and download the fglrx driver from ATI.  Is this common?  This is probably why my splash screen forze up and I could even boot into the live CD.

[SIZE="4"]**Network Card Issue:**[/SIZE]
Next, my wireless network didn't get started right out of the box.  It was detected and worked fine in Ubuntu 6.06.  I actually fixed this issue on my own this time...I feel like I am getting smarter with Linux everyday....no forum help on this one. 8) 

Anyway, what I noticed was, Ubuntu was recognizing my WMP54G (rt2500 chipset) wireless card with no issue!  That is great, except it did not name the interface as wlan0, it called it ra0!

So, I had to edit the file /etc/network/interfaces and add the following lines:
```

auto ra0
iface ra0 inet dhcp
```

Once I added these lines, I could go into the Network Manager and setup the ESSID and WEP Key.  Again, should I report the fact that this card is given the interface name ra0 and not wlan0?

Also, is there a way to change the interface name to wlan0?  In network manager my ethernet interface says Ethernet Interface, but my wireless interface (ra0) says Unknown Interface.  I have this hunch that if I can change the ra0 interface to wlan0, then Wireless Interface would show up in the Network Manager, correct?


Ok, so should I report those two issues and if so, where?

And can anyway answer the other questions scattered throughout there, like in my wireless section?

Thanks, love Ubuntu, LOVE the community! :D 
~Jon

---

### Post by jimbren on 2006-11-18
Well, since you already posted your issues in absolute beginner talk, I would not repost them anywhere else--that just makes it hard to keep track of the advise you get, and cross-posting is a generally Bad Thing to do anyway.  

Normally, you would probably want to post these questions to the installation and upgrades subforum, but there's really no harm in posting here.  

As to the question of is it worth it, I would say that it definitely is.  The Ubuntuforums community is very supportive and knowledgeable.  

Other than that, I haven't got any familiarity with your specific issue.  So I'm really not any help at all.  :mrgreen: 

jimbo

---

### Post by PriceChild on 2006-11-18
You should search [http://bugs.ubuntu.com](http://bugs.ubuntu.com) to see if the instillation issues about your hardware not being detected properly are already present.

If they aren't then report a bug for each item :D

---

