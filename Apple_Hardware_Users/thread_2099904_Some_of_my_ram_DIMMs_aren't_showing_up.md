---
title: "Some of my ram DIMMs aren't showing up"
date: 2012-12-31
forum: Apple Hardware Users
---

### Post by cellarweasel on 2012-12-31
Hello everybody with powerpc's,
I'm looking to find a way of identifying which ram slots are used. Unfortunately I have 3 gigs worth of DIMMs installed but only 1.5GB of memory show up as recognized by /proc/MemTotal or in System Monitor. 

I found how to do this with intel/amd architecture but it requires the BIOS in the machines to be read with [[COLOR="DarkSlateBlue"]dmidecode[/COLOR]]("http://www.cyberciti.biz/tips/plan-for-linux-server-memory-upgrade.html"). As this is a powermac G5 dual 2.5ghz dmidecode isn't even in the powerpc repositories. 

How do you all find which ram slots are being used?

---

### Post by chadk5utc on 2012-12-31
try this you may have to scroll and look for it
dmidecode -q | less
it will output a lot of info but your looking for something like this
> Memory Device
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_3
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: 0000000000000000
        Serial Number: 00000000
        Asset Tag: 000000
        Part Number:     2G U64CP8-S6


---

### Post by cellarweasel on 2013-01-12
Dude, read the second half of my post. dmidecode **doesn't work with PowerPC**

I need advice about OpenFirmware aka OpenBoot. Anybody out there a Solaris admin? or a Old time X-Serve guru? Or a IBM POWER sysadmin? 

Any Unix Guru's out there that know about Firmware in general? Coreboot folks?

---

### Post by barbaGNU on 2013-01-13
ususally from OF you are able to see the installed ram:
```
> dev /memory@0
> .properties
```
 
Anyway remember to reset NVRAM/PRAM everytime you modify your hw configuration.

---

### Post by cellarweasel on 2013-01-14
Wow, thank you BarbaGNU. I needed a solid answer like that. 

May I ask you how you found my thread? As you can see I tried to put a lot of keywords in my second post so that it would be more search friendly.

---

### Post by barbaGNU on 2013-01-15
i'm glade you solved.
 
About tags... no, i don't. I simply/seldom read this forum interested in ppc topics.

---

### Post by cellarweasel on 2013-01-26
Hey BarbaGNU,
I have a follow up question.
After googling dev /memory@0 and .properties I found that you can set openfirmware to display base 10 instead of hexidecimal. But it doesn't in the memory's .properties. 
Any suggestions? 

Or should I just get out a scientific calculator and figure it out?

---

### Post by barbaGNU on 2013-01-27
no idea, sorry.

---

