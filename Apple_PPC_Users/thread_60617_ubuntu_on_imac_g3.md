---
title: "ubuntu on imac g3"
date: 2005-08-28
forum: Apple PPC Users
---

### Post by im_ka on 2005-08-28
any experiences with ubuntu on a imac g3, 500 mhz, 192 mb ram or similar config? 
just bought one on ebay and afaik it'd need more ram to run os x with a good speed. so i'm thinking about ubuntu... might do debian with xfce though...

ideas, recommendations?

---

### Post by DJ_Max on 2005-08-28
I've been running Ubuntu on a iMac G3 400MHZ w/ 256mb of RAM. And couldn't ask for anything else with Ubuntu.

---

### Post by im_ka on 2005-08-28
how about the flash and java issues? is there a workaround? afaik it's a general ppc linux thing

---

### Post by DJ_Max on 2005-08-28
[QUOTE=im_ka]how about the flash and java issues? is there a workaround? afaik it's a general ppc linux thing[/QUOTE]
 I don't use flash or Java for unreleated reasons. But the Wiki and  [http://powerpc.ubuntuguide.org](http://powerpc.ubuntuguide.org) has workarounds. For example, IBM has PPC Java implements, which I've used in the past and worked fine. There's also a open source implementation of Flash.

---

### Post by im_ka on 2005-08-28
[QUOTE=DJ_Max]I don't use flash or Java for unreleated reasons. But the Wiki and  [http://powerpc.ubuntuguide.org](http://powerpc.ubuntuguide.org) has workarounds. For example, IBM has PPC Java implements, which I've used in the past and worked fine. There's also a open source implementation of Flash.[/QUOTE]

sounds good to me. the only thing i need java for is my stupid netbanking thingie, and i can use my gf's laptop for that if nothing else works.

do you think a default ubuntu install with gnome would work fine with 192 mb ram... if so i'm gonna stop looking for ram modules on ebay :)

---

### Post by DJ_Max on 2005-08-28
I would say so, as long as your Java program isn't too resource hungary, as most Java apps are. But more RAM the better. I got my RAM mod off of eBay as well. Seeing as I'm an eBay fanatic.

I don't have much more RAM then you, and I usually have
Desktop #1
Firefox w/ about 4 tabs, Gaim, and Terminal

Desktop #2
Alltray Terminal, Synaptic

Desktop #3
Scite, Terminal, for Ruby programming, and sometimes C++ compiling

Desktop #4
Gimp and the Eye of Gnome for random image editing/creating.

And it runs like a champ.

---

### Post by im_ka on 2005-08-28
[QUOTE=DJ_Max]I would say so, as long as your Java program isn't too resource hungary, as most Java apps are. But more RAM the better. I got my RAM mod off of eBay as well. Seeing as I'm an eBay fanatic.

I don't have much more RAM then you, and I usually have
Desktop #1
Firefox w/ about 4 tabs, Gaim, and Terminal

Desktop #2
Alltray Terminal, Synaptic

Desktop #3
Scite, Terminal, for Ruby programming, and sometimes C++ compiling

Desktop #4
Gimp and the Eye of Gnome for random image editing/creating.

And it runs like a champ.[/QUOTE]

that sounds pretty good. i use gnome with 2 virtual desktops enabled, and most of the time use only one. i keep the second one for nautilus ftp.

the machine isn't here yet, but i assume that those imacs got two slots for ram, in my case probably 128 + 64 - or am i wrong here?? so i might replace the 64 mb one with another 128 module. i mean i'm running ubuntu now on my thinkpad with 256 and it's all nice, and i guess there shouldnt be much difference.

btw, apple is no different than m$: you need more and more resources with every new version of their os. only that they make nice hardware... hmm i'm gonna love that blue imac on my desk :)

---

### Post by im_ka on 2005-08-28
i checked the ubuntu ppc wiki. didn't know there was such thing, definetly gonna join in soon ;)

---

### Post by DirtDawg on 2005-08-28
I have an Imac G3 as well. I've tried Mandriva, Yellow Dawg, and something else (but I don't remember what). Ubuntu has been hands down the best. Highly recommended from this user.

---

### Post by DJ_Max on 2005-08-29
[QUOTE=DirtDawg]I have an Imac G3 as well. I've tried Mandriva, Yellow Dawg, and something else (but I don't remember what). Ubuntu has been hands down the best. Highly recommended from this user.[/QUOTE]
 I tried both Yellodog and Mandriva, as well, and Ubuntu blows them away. Both Yellowdog and Mandrivia are both commercial type, as you have to pay for the newer versions.

>  but i assume that those imacs got two slots for ram, in my case probably 128 + 64 - or am i wrong here??
Yep, you're right. Two RAM slots underneath, super easy to replace, just get a penny and turn the knob, and stick em in there.

> i checked the ubuntu ppc wiki. didn't know there was such thing, definetly gonna join in soon 
Yeah I started that a bit ago. Just got a real domain a few months ago.

---

### Post by iiJeebz on 2005-08-29
I also run Ubuntu ona G3 400MHz, with 512MB RAM... I find it 'acceptable' in terms of performance. Mind you, I really only use this machine for general net duties i.e email, usenet, www and the like. 
But in general, everything loads and runs at a good speed... I have a couple of smallish problems with this install (such as it not keeping the refresh rate I set) but apart from that I'm really very happly with it.

I say go for it.

---

### Post by im_ka on 2005-08-30
[QUOTE=DirtDawg]I have an Imac G3 as well.[/QUOTE]

how much ram?

---

### Post by DirtDawg on 2005-08-30
[QUOTE=im_ka]how much ram?[/QUOTE]

You know, I'm not exactly sure and I've been wondering about that. I haven't checked since the os was still Mac OS9 (before I really knew what RAM was). What command can I use to find the specs of my box?

---

### Post by DJ_Max on 2005-08-30
[QUOTE=DirtDawg]You know, I'm not exactly sure and I've been wondering about that. I haven't checked since the os was still Mac OS9 (before I really knew what RAM was). What command can I use to find the specs of my box?[/QUOTE]
 ```
cat /proc/meminfo
```

---

### Post by DirtDawg on 2005-08-30
[QUOTE=DJ_Max]```
cat /proc/meminfo
```[/QUOTE]

Thank you. Unfortunately, I don't understand the output of this command. Could someone act as a rosetta stone?
```

MemTotal:       320672 kB
MemFree:        133168 kB
Buffers:          8200 kB
Cached:          87680 kB
SwapCached:          0 kB
Active:         110708 kB
Inactive:        58368 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       320672 kB
LowFree:        133168 kB
SwapTotal:      445228 kB
SwapFree:       445228 kB
Dirty:             748 kB
Writeback:           0 kB
Mapped:          99460 kB
Slab:            11616 kB
CommitLimit:    605564 kB
Committed_AS:   140688 kB
PageTables:       1308 kB
VmallocTotal:   645456 kB
VmallocUsed:     16592 kB
VmallocChunk:   627532 kB

```

---

### Post by DJ_Max on 2005-08-30
[QUOTE=DirtDawg]Thank you. Unfortunately, I don't understand the output of this command. Could someone act as a rosetta stone?
```

MemTotal:       320672 kB
MemFree:        133168 kB
Buffers:          8200 kB
Cached:          87680 kB
SwapCached:          0 kB
Active:         110708 kB
Inactive:        58368 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       320672 kB
LowFree:        133168 kB
SwapTotal:      445228 kB
SwapFree:       445228 kB
Dirty:             748 kB
Writeback:           0 kB
Mapped:          99460 kB
Slab:            11616 kB
CommitLimit:    605564 kB
Committed_AS:   140688 kB
PageTables:       1308 kB
VmallocTotal:   645456 kB
VmallocUsed:     16592 kB
VmallocChunk:   627532 kB

```[/QUOTE]
 You have 320MB of Ram. So I'm guessing you have the factory default 64MB stick, plus an added 256MB stick.

---

### Post by im_ka on 2005-08-30
everyone has more ram than me :(
looking at some offers on ebay... but i real wanted to keep this machine as-it-is

---

### Post by DirtDawg on 2005-08-30
[QUOTE=im_ka]everyone has more ram than me :(
looking at some offers on ebay... but i real wanted to keep this machine as-it-is[/QUOTE]
Thanks to DJMax. 
I have only about 130 more RAM than you and my machine runs Ubuntu very well. Firefox, Openoffice and GIMP take 10 seconds or so to open, but most everything runs smoothly and quickly including Blender and Inkscape. I would recommend trying Ubuntu out to see how it runs on your RAM. It may work well enough to keep you happy as is.

---

### Post by airbon on 2005-08-31
can anyone watch DVD or DIvx movies at acceptable speed?

---

### Post by im_ka on 2005-08-31
it's not exactly fast, but usable. gonna buy more ram as soon as i have the money.
ubuntu is the first ppc linux i've tried, and i don't think i wanna try another one :)

---

### Post by airbon on 2005-09-01
I have a G3 600Mhz ibook with 640Mb RAM, actually it belong to my wife. I actually replaced the 20gb hdd with an 80gb and add 512Mb RAM. I just can't seem to get an acceptable frame rate out of it. It is always skippping frame when i play DVD or Divx movies. any suggestion.

---

### Post by hndrcks on 2005-09-03
Suggestion: in Intel - land, these symptoms would indicate that the DVD player is not using DMA (direct memory access) during playback. I have seen 2 gig Intel processors drop frames when DMA isn't activated.

---

