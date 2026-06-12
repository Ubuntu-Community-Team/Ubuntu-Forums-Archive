---
title: "Need BIOS Advice..."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-06-07
Sigh, I managed to damage my BIOS, first time too (really, 15 years and it was always something else that got my computers first). Guess now I can say I done almost everything to a computer ^^. Anyway... I was just doing a simple back up with my Acronis True Image bootable CD. I finished the back up and then the computer froze... I tried to quit the program but it was locked up and I had to manually reset. Then it seemed to give me problems. :(

It just seems kinda flaky after that. I know it completes the POST on start up right, I think. But when it pops up with the IBM splash screen that usually lasted a second (before the freeze) it sits there... for almost a minute. Like its waiting for something. Then the screen flashses black and tells me its starting the intel boot agent (didn't flash me that message before the crash) and then it gives a very loud beep from the internal speaker (didn't do that either before). I was content to leave it with the delay, but it seems to be going down hill as last two times I booted it gave me trouble at the boot agent screen and I had to reset to get in.

So help please.... I'm not sure what to do and I don't wanna have a 20+ pound brick in my room (not to mention no more me around forums if its dead >.>). I did a bit of looking around and I found my [model on the IBM support site.]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952") It gives me 3 options to flash, via floppy, cd or XP.... which ones recommended/safer? Will that work even if its somewhat damaged? I think I can still get the boot options even if its flaky... Another question, should I maybe look at one of the open bios projects or are they not really ready yet? Hope someone can answer, I'm kinda wary to restart again without knowing what to do....

---

### Post by mlentink on 2007-06-07
Starcraft.man, i hear you.

I used to be a bit of a hardware guy (long ago in a galaxy far away). My first instinct is that it is not your BIOS that is kaputt, but your boot sector. BIOSes are specialized devices that cannot be flashed without special software. I sincerely doubt Acronis would be so foolish as to incorporate that in their backup stuff.
I'd check out the boot sector first.
If you then really have to flash your bios, I would personally prefer to use a floppy, because they are simple devices recognized by all bioses. Second choice is the cd which I see they also support. For obvious reasons the OS versions does not apply to you...

---

### Post by chili555 on 2007-06-07
I see nothing in your description that suggests the BIOS has gone flakey. Usually, when the BIOS gets to the Intel boot agent, it means it has cycled through the harddrives, CDROM and floppy and now thinks the network boot is next to try. This supports the idea that the boot sector on the harddrive is damaged.

Have you searched for the beep codes for your particular model? One long beep surely is telling you something important.

Will it boot the live CD?

---

### Post by pappapump on 2007-06-07
One long beep means a failed battery.
Just pop out your bios battery and do a voltage check.
It should read above 3 volts to be good.
Some bios can tolerate 2.8 but IBM is pretty picky.

---

### Post by Malta paul on 2007-06-07
As the last post said I don't think you have trashed your bios. Have you tried reseting it?  The bios settings are retained in memory by a small button battery. If you remove the battery [ switch OFF the computer first and disconnecting the power lead so as not to damage your motherboard] refit the battery and your bios will be set to the default. If this works for you you can then fine tune you bios settings as you wish.
Hope this is of help, good luck ;)

---

### Post by starcraft.man on 2007-06-07
Hmmm, ok thanks for quick reply. So its split between my boot sector and the battery? I got a copy of the floppy BIOS flash just in case...

How do I check the boot sector for consistency if thats the problem? If its bad what do I do?

If it is the battery? Is this what your talking about in the pictures? [Link.]("http://www.hardwaresecrets.com/article/81") I never pulled it out before so wanna make sure I pull the right thing... How exactly would it get drained anyway, I mean my desktop's always plugged in... just goes bad over time? If its bad, they standard and cheap to replace?

I gotta tell ya my Ol' Netvista case is a pain to get to things (small case, I should probably get a replacement one day) so I don't wanna have to mess around too much in there (you really wouldn't wanna see the mess I made in it...).

---

### Post by information_entropy on 2007-06-07
Yes those are pictures of the the good old CR2032 battery that many motherboards use
You should read the numbers on the battery in your computer to verify exactly what one your computer uses.  

They cost a couple of dollars, they are not expensive.

If the computer is old then replacing is will not hurt, like any battery they do not last forever.

Be very careful to not fold, bend, or mutilate the metal bracket that is holding the battery in.
I have seen many motherboards damaged beyond repair because of a botched attempt to replace the CMOS battery.

Your problem, as others have stated, could be the hard drive boot sector,
but a worn out battery is also a possibility.

Personally, I would replace the battery and see what happens.
Always try the cheapest/easiest solution first.:)

---

### Post by mlentink on 2007-06-07
> **information_entropy said:**
> 
Personally, I would replace the battery and see what happens.
Always try the cheapest/easiest solution first.:)

so true!

---

### Post by Malta paul on 2007-06-07
If you have the handbook for your mother board it should tell you which jumper pins to short-out, to rest your bios with out removing the battery. Removing the battery is no problem though and will not damage your motherboard _provided _you switch of the power. Your battery is probably OK as your bios clock would need resetting after the computer had been shut down for a while. ;)

---

### Post by Atomic Dog on 2007-06-07
> **Malta paul said:**
> If you have the handbook for your mother board it should tell you which jumper pins to short-out, to rest your bios with out removing the battery. Removing the battery is no problem though and will not damage your motherboard _provided _you switch of the power. Your battery is probably OK as your bios clock would need resetting after the computer had been shut down for a while. ;)

If you're lucky you can download the MB manual online to find the right jumper.  If you're really lucky the MB will actually have BIOS written by the jumper.  Couldn't hurt to pull out a flashlight and look at the board if you can't DL the manual.

---

### Post by starcraft.man on 2007-06-07
Ok  thanks for all the help. I think its fixed... I pulled out the battery and checked it and it was fine, popped it back in and I haven't gotten any more error messages at boot. I'll probably go get a new one just in case on the weekend. It's still a bit slow to get rid of the IBM splash but I guess long as its still working thats fine.

I probably just need a new computer... a 6 year old PC is the oldest I've ever had......

---

### Post by southernman on 2007-06-07
By pulling out the battery, what you in essence did was "reset the bios." With that said, it can't hurt to flash the bios to the latest stable release.

Flashing the bios can be scary... just follow the instructions without fail and you'll be fine.

I prefer to not see splash screens during post. This way, you see the normal post messages scroll across your screen instead of the deep hidden satanic messages stored away in those useless splash screens. ;)

---

### Post by poe503 on 2007-06-07
In my Netvista board, you have to set the jumper and then turn on the computer for 10 seconds to reset the BIOS which is quite different from the usual SOP.  You can still download manuals for Netvista from Lenovo, not IBM.

---

### Post by mlentink on 2007-06-07
> **southernman said:**
> By pulling out the battery, what you in essence did was "reset the bios." With that said, it can't hurt to flash the bios to the latest stable release.
Hmm.
I always thought that you were resetting CMOS RAM, in which more or less persistent config data is stored, which the BIOS makes use of.  A BIOS needs to be flashed, so cannot really be reset that way, afaik,

Still, it won;t really hurt to update to the newest version....

---

### Post by southernman on 2007-06-07
My fault! I did say that wrong... it is the CMOS that was reset, not the bios. Removing the battery, or moving the jumper does the same thing.

*reminds himself to slow down* 

duhhh!

---

