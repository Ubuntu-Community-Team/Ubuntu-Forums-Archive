---
title: "No Apple wireless, 9800XT, 20&quot; Cinema Display support yet?"
date: 2005-03-11
forum: Apple PPC Users
---

### Post by brent1a on 2005-03-11
I'm running Ubuntu 5.04 Preview LiveCD on a dual 2.5 PowerMac with (factory) bluetooth mouse and keyboard and a 9800XT video card. Are these supported yet? I get thru all the process of detecting hardware and loading for Ubuntu Live just fine but I get some errors loading something (it all zooms by so fast) and then after it says a few more things are loaded 'ok' my screen (20"  Cinema Display) goes to sleep. I can only assume that Ubuntu and Gnome have loaded fine just that some of my hardware isn't compatible yet?

---

### Post by brent1a on 2005-03-16
Wow, great! Thanks for all the great suggestions. Jeez you'd think that at least 1 Ubuntu developer would browse through the forums once in a while. 55 viewings of my thread and not 1 single suggestion. I'm glad I didn't try to actually install this on my hard drive or anything I would've been totally pooch-screwed.

---

### Post by kadymae on 2005-03-16
Here's a partial list of supported hardware.

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesDesktops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesDesktops)

and
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)

Note that the 9800xt series cards are not listed.

---

### Post by brent1a on 2005-03-16
Thanks.....guess I could've eventually found that on my own. I guess, as it stands, I was a bit too overzealous and naive in my quest for a stable linux to work on my G5. I guess my hardware is just too advanced for the current linux kernel? I don't know, I tried linux on my old PC about a year ago and almost destroyed three city blocks in an enfuriated rage of disappointment and disbelief (my system was 3 years old and still too advanced for the then current SuSe) and I'm glad I didn't attempt that with my $5000 G5.

---

### Post by poofyhairguy on 2005-03-16
[QUOTE=brent1a] I guess my hardware is just too advanced for the current linux kernel? [/QUOTE]

No. ATI just won't release PPC drivers. Those that get their Apples to work have cards that are older than the 9200 (that have open source drivers).

It's not linux's fault ATI blows. If you were a x86 person, I would say sell your ATI card on ebay and get a Nvidia one.. But as a Mac man (or woman), I suggest just using OSX instead.

---

### Post by daniels on 2005-03-16
Er, poofyhairguy, you do realise that 2D will work just fine on the 9800XT?  And, given that nVidia don't release their binary drivers for the PowerPC either, you won't get 3D on a PPC with any nVidia card?

brent1a, now that I've finished with xorg 6.8.2-4 and 6.8.2-5 (which has consumed a lazy 25 of the last 29 hours of my life), I was going through the bugs I had to follow that one up, because I seem to recall a possible way to get that working; 'I don't know, wait a while while I chase it up' isn't a terribly useful response, so I figured there wasn't much point in it.  Oh well.

---

### Post by daniels on 2005-03-16
For what it's worth, as far as I can tell (given that I don't own one of these beasts), the fix for your video woes is to put this in the Monitor section of xorg.conf:
```
ModeLine	"1680x1050" 147.1 1680 1784 1968 2256 1050 1051 1054 1087
```

---

### Post by brent1a on 2005-03-17
I appreciate your help but I'll have to admit that advice is a little, correction, A LOT out of my league. It's not your fault, in fact I'm probably still harboring resentment left over from my failed experience with SuSE.

---

### Post by poofyhairguy on 2005-03-21
[QUOTE=daniels]Er, poofyhairguy, you do realise that 2D will work just fine on the 9800XT? [/QUOTE]

Yes. But I also realize that it uses generic drivers, so other special stuff  (aka more than 3D) is out the windows as well...

---

### Post by daniels on 2005-03-21
Yeah, you don't get 3D acceleration.  But everything else generally works fine.

---

