---
title: "should i just reinstall?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by feelie88 on 2007-07-25
alright, i have a kinda working feisty installed on my computer (it freezes nonstop) but when it works it's great. I installed the 32bit version on a 64bit amd 3600+ brisbane. I heard that the 64 bit version runs faster than the 32bit and I'm just wondering if it's better to do a fresh reinstall of the 64bit, or try to fix my install...

the only reason i'm asking this is that i had to go through a lot crap to get this install going (my rt61 wifi card wasn't supported, my intergrated graphics weren't supported, when i leave x my monitor stops responding, etc.)

what should i do, and if i should stay with my install can anyone help with the freezing? I already installed the new 386 kernel but the freezing still persists...

thank you in advance for reading this

---

### Post by be4truth on 2007-07-25
I have 32bit version running on quite some 64bit machines without any problems. I think the 64bit version are less stable than the 32bit ones which means more trouble.
It is hard to say why your set-up freezes. Pls give more detail. How do you install?

---

### Post by threeonethree on 2007-07-25
mayb it hangs because the dma is off or the hard drive is about to go kaput?

try sudo hdparm /dev/hda(or w.e ur drive is , sda1 or sda2 or hda2) and see if dma is turned on

---

### Post by feelie88 on 2007-07-25
thanks for the speedy replies!

I'm at work right now so i can't do anything to my pc just yet but i can answer a few questions.

my hardware:

mobo: biostar tf7050 pv
hard drive: ide 6.4gb, and sata 200gb (i installed ubuntu on the ide and the sata is not formatted yet(windows))
memory: 2x1gb super talent ddr2 800
wireless nic: msi pc60g based on the rt61 chipset

I installed using the safe graphics mode because the regular way did not recoginize my internal graphics (nvidia just released the new drivers one month ago)

i don't have constant internet access because my wifi is spotty at best (me and my neighbor share a wifi connection and my room is the furthest room in my house from his router...he can't move his because his dad needs it in that position...)

the hdd might be going kaput, it IS very old...and now that i found out that windows can write to ext3 there is no excuse for me to have ubuntu on the small hdd and windows on the big one.

I had install the serial monkey drivers to get my internet going and it all worked fine in our living room. I would just type in "sudo dhclient ra1" and it would connect but after installing wifi radar and moving the comp upstairs, my connection sucked and i started to notice the freezing. i uninstalled wifi radar and installed wicd and my computer freezes less but it does still freeze a lot.

i ordered an extension cable for my antenna (and built a cantenna) and it should get here by friday, once that is in we can find out if it's an internet problem or not...

---

### Post by dptxp on 2007-07-25
Reinstall 64 bit.
In case of any problems, post in the 64bit forum.

Has the person who says that 64 bit is less stable actually used it ?

I use both 32 bit and 64 bit (on 2 different machines)

---

### Post by feelie88 on 2007-07-25
the guy said that 64bit is harder to use and doesn't have all the programs that the 32bit does, because it's so new.

I'll download a 64bit cd and install it on my other hdd, that way if anything goes wrong i can just reinstall.

do you know if serialmonkey has released 64bit drivers yet?

---

### Post by be4truth on 2007-07-25
This a funny thread. If you ask 'Shall I reinstall' some will say yes others no. At the end of the day you have to decide yourself anyway - or post another thread:).
Have a look here

[http://ubuntuforums.org/forumdisplay.php?f=134]("http://ubuntuforums.org/forumdisplay.php?f=134")

---

### Post by dptxp on 2007-07-25
> **feelie88 said:**
> the guy said that 64bit is harder to use and doesn't have all the programs that the 32bit does, because it's so new.

I'll download a 64bit cd and install it on my other hdd, that way if anything goes wrong i can just reinstall.

do you know if serialmonkey has released 64bit drivers yet?

There is nothing wrong in using 32 bit. 
But 64 bit is not harder to use, has almost all programs that are in 32 bit and there are ways to run 32 bit programs in 64 bit (I have not yet felt the need in my 64 bit OS).
The 64 bit section in the forums shall take care of any question, problems or help you need.
[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)
It is quite fast in number crunching programs as image editing, audio and video conversions etc.

You can go to packages.ubuntu.com and check for yourself, it will be hard to find programs that are in 32 bit but not 64 bit.
And it is rock solid.

You can even install both 32 bit and 64 bit, just 6 GB extra for another / (root) and check for yourself.

---

