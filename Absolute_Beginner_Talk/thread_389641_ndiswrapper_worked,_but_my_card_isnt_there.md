---
title: "ndiswrapper worked, but my card isnt there"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by thejones on 2007-03-21
ok, first off, my problem involves my broadcom 4311 and DSL-N. i know its not ububntu, but i figured that someone here might be able to help me.

i finaly got ndiswrapper to load my driver (turns out i had a bad copy), but my wireless still wont work.;

after i install bcmwl5.inf i run this:```
ndiswrapper -l 
``` and it shows that driver and hardware are installed.

then i do ```
sudo ndiswrapper -m
``` and it say something about allies wlan0. normal so far (i think...)

then i try ```
sudo iwconfig wlan0 
``` and it tells me that there is no such device.

then just to see what happens, i tried the next step: ```
sude iwconfig wlan0 "my ssid" key "my wep"
``` and it said that if failed at wireless device and that is doesnt exist.

i thought everything was working up to this point, but then my card wont show up. am i missing a step? 

like i said, this is all in damn small linux-not. and it is being loaded from a 256mb flash drive. i have been running it this way ever since i screwed up my first ubuntu install (dual booting with xp) and grub spazed out so bad that i had to wipe myentire hard drive (im sure there were other options, but i wanted to start clean.).

my thinking is that if i screw this up, i can wipe it and start over agian (and again, and again....) with little or no impact on the rest of my system. at least that the thought. could this problem be cuased by booting from the flash drive. i know that doing it this way is sub-optimum, as it hold everything in a single FAT partition. but that wouldnt effect this, would it?

AAARG !! ](*,)

---

### Post by bwingbob on 2007-03-21
> ```
Code:

sudo iwconfig wlan0


```

try ```
sudo iwconfig
``` without the wlan0.

When you ndiswrapper -m the light on your wireless adapter should have starting blinking, did it?

---

### Post by thejones on 2007-03-21
> **bwingbob said:**
> 

When you ndiswrapper -m the light on your wireless adapter should have starting blinking, did it?


no it doesnt.

my laptops wireless card has an orange light when its off and a blue light when its on. no blinking that i have ever seen.

and for what its worth, the light stays orange.

---

### Post by bwingbob on 2007-03-21
You might try a different version of you cards Windows driver.

I have a NetGear WG111V2 and I had to try several different versions of the driver before I found one that worked.

With the drivers that failed my wireless led would blink once when I did ndiswrapper -m.
With the one that finally worked the light kept on blinking once I did ndiswrapper -m.

One other quirk, if I boot with the adapter attached to the computer it will not work. If I wait until after the boot is complete and HOTPLUG it the adapter works fine and is very stable. 

This post may help you [Good Luck]("http://wiki.waningsun.net/index.php?title=Dell_E1405_%26_Linux_HOWTO")
PS.
I ended up with the 98 driver. None of the NT variants would work.



good luck.

---

### Post by da1nonlymikeo on 2007-03-21
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

 this worked perfectly for me. and it was really fast and simple. couldent believe it. give it a try?

---

### Post by bwingbob on 2007-03-22
> **bwingbob said:**
> try ```
sudo iwconfig
``` without the wlan0.

When you ndiswrapper -m the light on your wireless adapter should have starting blinking, did it?

I should have asked did the light blink when you did modprobe ndiswrapper?

> With the drivers that failed my wireless led would blink once when I did ndiswrapper -m.
With the one that finally worked the light kept on blinking once I did ndiswrapper -m.

This should have been modprobe ndiswrapper as well. 

Sorry, it was late when I replied. Let me know how you come out.

---

