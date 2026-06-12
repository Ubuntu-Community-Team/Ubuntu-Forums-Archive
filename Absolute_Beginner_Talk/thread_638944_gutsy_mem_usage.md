---
title: "gutsy mem usage"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-12
why does gutsy use much more memory than feisty?

im using the same styuff as fesity, aMSN, Swiftfox, Cmpiz Fusion and im using 500mb of RAM.

in feisty i used 250mb max.

i cant find whats using the extra 250mb

to be honest i think gutsy could have been better, seems they havent tried.

but ive heard rumours that 8.04 is supposed to be a speed machine :guitar:

---

### Post by ewr2san on 2007-12-12
What does top say?  Try sorting by mem usage (Capital M).

How much is being used by buffers, etc?

Im not seeing much difference in memory usage between Kubuntu Feisty and Kubuntu Gutsy.

---

### Post by skymera on 2007-12-12
19156k buffered

---

### Post by skymera on 2007-12-12
so that not help? ^_^

---

### Post by Majorix on 2007-12-12
There is not much difference on my machine either, although I have recently upgraded to Hardy. Back in Gutsy I could easily do my tasks on a 512mb ram machine.

---

### Post by skymera on 2007-12-12
i see. what is hardy like?

i know 512mb isnt much but its double what i was using, i just curious whats usning twice the ram?

---

### Post by ewr2san on 2007-12-13
So when you sort by memory usage in top (press Capital M), what processes are taking up the most memory?

---

### Post by skymera on 2007-12-13
Xorg
Wish
Swiftfox

---

### Post by linuxlizard on 2007-12-13
Hey that's interesting. I set my folks up with kubuntu fiesty and it zips along even though it's only got 256 mb ram. It can run everything and runs it well- even 3d beryl cube with bells and whistles and 3d games like urban terror. it's an old athlon 1800+ with a 64mb nvidia. All the talk lately about memory requirements have me spooked to upgrade their machine...

---

### Post by skymera on 2007-12-13
if it runs fine thats good :)

i cant seem to get anything mem usage down. :(

---

### Post by ewr2san on 2007-12-13
You are running xbuntu right?

Well, Fiesty was xorg 7.2   and Gutsy is  Xorg 7.3.
Any Idea how much memory xorg was using under 7.2 as compared with 7.3?

It also sounds like this is rather steady state and not the memory leak in the invida driver [http://www.nvnews.net/vbulletin/showthread.php?t=100640](http://www.nvnews.net/vbulletin/showthread.php?t=100640)

Also did you change video resolution? That would gobble a bit more memory.  

Im running kubuntu and booting back to my old feisty system image im not seeing any difference in memory usage.  So I suspect xorg more than anything else...  As a curiosity, you could boot off of the live cd's and compare feisty vs gibbon.

---

### Post by mcduck on 2007-12-13
Just to make sure that it's not just a case of cached/buffered data, try running 'free -m' and check the '+/- buffers/cache'-line to see the actual memory usage. This is much simpler way than using 'top' and trying to calculate the real memory usage from the data 'top' gives you..

Of course to check how much the system itself is using memory it would be a good idea to do this right after boot, without running any programs like Firefox that can use very much RAM depending on how long it has been open and what kind of pages you have visited.

---

