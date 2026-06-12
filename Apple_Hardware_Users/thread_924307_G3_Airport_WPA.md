---
title: "G3 Airport WPA"
date: 2008-09-19
forum: Apple Hardware Users
---

### Post by gaussian on 2008-09-19
Has anyone ever gotten Airport to work with WPA following the directions (that seem to work for our PC using friends) in [http://ubuntuforums.org/showthread.php?p=5148420#post5148420](http://ubuntuforums.org/showthread.php?p=5148420#post5148420)
?

I compiled the patched driver and it loads cleanly (from dmesg) when you first remove airport, orinoco and hermes drivers. The problem is that when I do that my wireless "network interface" disappears. Meaning, if I do: 
```

ifconfig

```

I don't have eth1 anymore. Only way to get eth1 back is to modprobe airport, but that loads the conflicting orinoco driver. Any ideas? My university will at some point disable WEP-based access and I can't blame them. I might just have to  dole out big bucks for an USB based card for this machine if I don't get it to work (Pismo laptop). Or I might get myself a Dell Mini with Ubuntu preloaded :) But I would prefer to solve the problem with no money involved.

---

### Post by gaussian on 2008-09-22
bump... After the predicted no responses to this bump I believe no one has figured this one out.

---

### Post by cyberdork33 on 2008-09-22
> **gaussian said:**
> bump... After the predicted no responses to this bump I believe no one has figured this one out.
I think you are waiting on someone with PPC experience to answer...

---

### Post by gaussian on 2008-09-22
> **cyberdork33 said:**
> I think you are waiting on someone with PPC experience to answer...

Yes, there does not seem to be too many of us around. G3 Pismo (with 640M of RAM) gives surprisingly adequate performance under Ubuntu. Under OS X it (10.4) it was painfully slow.

---

### Post by cyberdork33 on 2008-09-22
> **gaussian said:**
> Yes, there does not seem to be too many of us around. G3 Pismo (with 640M of RAM) gives surprisingly adequate performance under Ubuntu. Under OS X it (10.4) it was painfully slow.
I zombified my similarly spec'd iBook into a digital picture frame running OS X. It does indeed run slow.

---

### Post by jtappin on 2008-09-23
> **gaussian said:**
> Has anyone ever gotten Airport to work with WPA following the directions (that seem to work for our PC using friends) in [http://ubuntuforums.org/showthread.php?p=5148420#post5148420](http://ubuntuforums.org/showthread.php?p=5148420#post5148420)
?


While I'm not exactly up-to-date on this, I'm pretty sure that when I investigated this 2 or 3 years back I found that the original airport as used in the G3 iBook doesn't support WPA.

---

### Post by gaussian on 2008-09-23
> **jtappin said:**
> While I'm not exactly up-to-date on this, I'm pretty sure that when I investigated this 2 or 3 years back I found that the original airport as used in the G3 iBook doesn't support WPA.

You are fairly up to date on this. My understanding is that the chipset used in Airport supports WPA under a new Linux driver that has to be patched and compiled. Several people have successfully compiled that driver with Intel based computer (see the thread I refer in the beginning of this thread). That thread also includes few PPC Mac folks stating that "it does not work". What I was looking for any evidence that someone has gotten it to work.

---

### Post by theperson10 on 2008-10-30
> **jtappin said:**
> While I'm not exactly up-to-date on this, I'm pretty sure that when I investigated this 2 or 3 years back I found that the original airport as used in the G3 iBook doesn't support WPA.

Bumping, and explaining.
the original apple airport card, based on the orinoco chipset does support (and has **always **supported) wpa.
the module(s) currently used (airport+orinoco+hermes)was built under the assumption that the chipset does not, and therefore they do not support it either
apparently, someone has made an updated orinoco module that does not seem to work with PPC

---

### Post by caalamus on 2009-08-04
you guys are kinda talking over my head... but I halfway dig what you're saying. How about this:

I have a 500Mhz g3 iBook with 640MB/10Gb. Running 9.04.

Slowly but surely I'm getting it up & operational with a lot of research and help from the good people in this forum.

I have an original Airport card as well


lshw -C network

says:

<a href="http://photobucket.com" target="_blank"><img src="http://i168.photobucket.com/albums/u177/profanuscaalamus/2009/August/lshw-CnetworkE.jpg" border="0" alt="Photobucket"></a>


then running 

iwconfig 

results in:

<a href="http://photobucket.com" target="_blank"><img src="http://i168.photobucket.com/albums/u177/profanuscaalamus/2009/August/iwconfigE.jpg" border="0" alt="Photobucket"></a>

I gather that my system recognizes my airport card and that it is disabled...

do I need to download a driver... I see mention of "orinoco"?



any thoughts?

---

