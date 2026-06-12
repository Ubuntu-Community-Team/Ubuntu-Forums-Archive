---
title: "sigh.... maybe someone can figure this out"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by ekz13 on 2006-09-21
same issues as everyone else... tried..

6.06 live Ubuntu
6.06 install Ubuntu
6.06 live/inst Kubuntu
5.10 Breezy

nothing works, I either get a bunch of code and it kills at "kernal panic...init" or something like that (can post later) or it just hangs at the splash screen about 1/4 way through and does nothing..

trying to dual boot it (grub seems ok atm) for the moment to see if I like it or not.. but I can't get a working version at all, went through several cd's, different speeds, verified disk, tried the "boot=", etc, images, etc.. been working on this one for about 4 days now.  Any ideas?  Getting very frustrated, not sure if this is fixable or should I try a different distro (would really like to get Ub to work though)

---

### Post by Metacarpal on 2006-09-21
Hi - we'll be happy to help you.  Just need a bit more info...

Were the CDs you were using ordered through ShipIt, or did you download them?  If downloaded, did you check the MD5sum to verify that it downloaded right? (if you're not sure what that is, we'll help with that, too)

When you say it hangs up on the boot screen, is that the boot screen for the installation, or have you already installed and are attempting to use the installed Ubuntu system?

Also, tell us what kind of hardware you have.  What kind of processor do you have (Pentium2, Pentium3, Celeron, AMD64, etc) and what's the speed of it (900MHz, 2.0GHz, 333MHz, etc).  How many MB of RAM do you have?  How big is your hard drive?  How are you connecting to the internet?

There are a number of factors that can complicate the installation of a operating system, whether it's Ubuntu, another Linux distro, Windows, whatever.  The more we know about your system, the more we can do to help eliminate whatever problem stands in your way.

---

### Post by xpod on 2006-09-21
Probably be quicker trying the "alternate cd".....Lots of people have trouble with the live cd version..EVEN with decent specs.
Just a thought;
Good luck with it anyway

---

### Post by ekz13 on 2006-09-21
oops, yes that prob would help huh, sry... They were the .iso's from the website, my system is a compaq (celeron 2.3) with tweaked ram and vid card (nvida chipset, maddog card).. the livecd, gets to the code where I get the "kernal Panic" message and halts, the installs will either get to the brown ubuntu load and stop (can't remember what step exactly) and the Kubuntu will halt at the same place.

---

### Post by Bewildered on 2006-09-21
Tried to update V.5.04 to 6.06LTS a while back but got "Error 15" msg.
Can boot up with 6.06 and try to install, but hangs up when configures. Very new at this so make it simple out there if any one responds to this plea for help. Thanks.

---

### Post by Metacarpal on 2006-09-21
> **ekz13 said:**
> oops, yes that prob would help huh, sry... They were the .iso's from the website, my system is a compaq (celeron 2.3) with tweaked ram and vid card (nvida chipset, maddog card).. the livecd, gets to the code where I get the "kernal Panic" message and halts, the installs will either get to the brown ubuntu load and stop (can't remember what step exactly) and the Kubuntu will halt at the same place.

Have you tried using the "alternate install CD"?  Some people find the LiveCD doesn't get along with their systems, even if the specs are up to code (as previously noted by xpod)

---

### Post by ekz13 on 2006-09-21
I'll give that a shot, that's the one build I didn't try, I'll give that a whirl and let ya'll know.. Thanks! :)

---

### Post by Metacarpal on 2006-09-21
Keep us posted!

...um, as it were.

---

### Post by gn2 on 2006-09-21
If you still don't get anywhere, perhaps reset the BIOS to defaults.....?

---

### Post by CatKiller on 2006-09-21
> **ekz13 said:**
> oops, yes that prob would help huh, sry... They were the .iso's from the website, my system is a compaq (celeron 2.3) with tweaked ram and vid card (nvida chipset, maddog card).. the livecd, gets to the code where I get the "kernal Panic" message and halts, the installs will either get to the brown ubuntu load and stop (can't remember what step exactly) and the Kubuntu will halt at the same place.

How is your memory tweaked? If you've overclocked it, then that will probably cause you problems. A kernel panic is a Bad Thing.

---

### Post by ekz13 on 2006-09-21
perhaps tweaked is a bad word.. nothing is overclocked, by tweaked I mean, I replaced the crappy vid card with a better one, took the 256mg ram up to 768mg for better performance, that kind of tweaked, just took the out of the box system (rather than custom built and improved it for my needs, gaming, speed, etc)

---

### Post by CatKiller on 2006-09-21
Fair enough. I believe that it's the kernel panic that's the problem. Fix whatever's causing that, and you should be good to go. Out of my depth though, unfortunately. Sorry.

You could try the memtest86 (or whatever it's called) from the Live cd to see if you're having memory problems. It takes a little while to get through the tests, so you could leave it running overnight while you're in bed.

---

### Post by ekz13 on 2006-09-22
ok, downloaded the alt install and that went with no luck.. I kept hanging up as well, on the loading hardware drivers step, when I went to launch in recovery mode it locked in the same place as well.. the error message is 

"Kernal Panic - not syncing: fatal exception in interupt"

any ideas on this one?

---

### Post by ekz13 on 2006-09-22
one more thing...it did install ok I guess, I got the message for the login, the boot didn't go

---

### Post by YeahBuntu on 2006-09-22
I believe all of the distros come with memtest.  You should run it.

I would say you have either a memory problem or possibly some bad sectors on your hard drive that is flubbing everything.  grab a copy of GWscan (my favorite hard drive tool) from gateway and check the hard drive.  If it all comes out ok try writing zeros to the drive and try again with the alternate CD.

---

### Post by 3rdalbum on 2006-09-22
I haven't experienced this, but I've heard it mentioned that Linux doesn't like "uneven memory". Uneven Memory is where you have different capacity RAM chips in different slots. For instance, 512 in one slot, 256 in another.

I've got very uneven memory and everything works fine, but since you mentioned upgrading the RAM, and mentioned an odd number, it's possible that might be the problem.

---

### Post by ekz13 on 2006-09-22
Ahh didn't know about the mem chips, yes I'm running 2 banks.. 512 & 256.. is this a definate thing, or hearsay? I'm running the memtest, will report back when I get home on that one..

---

### Post by crokett on 2006-09-22
Another suggestion for you if nothing else pans out. Strip the machine down to as simple as possible.  If you have two HDDs, remove the one that you don't boot from.  Disconnect all USB devices - printers, etc.  Get down to 1 stick of RAM.  If that works, start adding stuff back till it breaks.

---

### Post by CatKiller on 2006-09-22
> **ekz13 said:**
> ok, downloaded the alt install and that went with no luck.. I kept hanging up as well, on the loading hardware drivers step, when I went to launch in recovery mode it locked in the same place as well.. the error message is 

"Kernal Panic - not syncing: fatal exception in interupt"

any ideas on this one?

Sounds like some kind of IRQ conflict to me. I know that when I installed Breezy it didn't like sharing IRQs any more, although Hoary had been fine. I didn't get a kernel panic though, my network card just didn't work. You may find that shuffling the cards around to minimise the number of shared IRQs will help. If you press the Pause button as your computer boots - after the memory test, but before grub has done its thing - you'll be able to read which IRQ has been assigned to each device. It's a bit of a kludge, and made me think it was 1994 again, but you may find that it works.

As to the different sizes of memory thing, I think that's nonsense. I have 320 MB in my computer, a 256 and a 64, and it works fine. I suspect it might be hearsay based on a particular motherboard chipset at a particular time, but I've never heard that claim before to have ascertained its veracity.

---

### Post by ekz13 on 2006-09-22
I was going to strip it down to nada and add it back in one by one, but really don't want to go that way if I can avoid it (just a PITA!) LOL... but I did fine something interesting (I think) when I tried to install SuSe 10.1, I did the cd install minimal and had it try to connect via the net to d/l the rest.. anyway.. it couldn't recognize my onboard nic, maybe that's the issue..hummm.. i'm going to try to see what that's is IRQ'd to when I get home see if there's a conflict.. glad to hear about the memory thing, that would kinda blow to have to replace my memory

---

### Post by ekz13 on 2006-09-23
ok, posting this from Kubuntu...managed to get it installed and running, so far so good... little issues to work out, but nothing major (I think) for those curious, I started to remove everything one by one in the bios, came to the conclusion that it was my vid card that was messing the whole thing up (nvidia 5200) just would not work, so I switched back to my onboard one... continuing my education...

---

### Post by CaveRat on 2006-09-23
> **ekz13 said:**
> ok, posting this from Kubuntu...managed to get it installed and running, so far so good... little issues to work out, but nothing major (I think) for those curious, I started to remove everything one by one in the bios, came to the conclusion that it was my vid card that was messing the whole thing up (nvidia 5200) just would not work, so I switched back to my onboard one... continuing my education...

Hmm! A question of curiosity? Was the onboard video enabled in Bios with the Nvidia chipset card also installed?

---

### Post by xpod on 2006-09-23
> ok, posting this from Kubuntu.

I could`nt get "ubu" on my compaq either and ended up with "kubunto" on it instead.....Glad though cause now we have both without having to do the dual desktop thing...

Its an older thing though and dont have a card like yours....has some "utah 64" onboard thing which is crap but does for what the kids use it for..
It had a card but i took it out as it was`nt working and looked a bit worse for the wear...

Glad to hear you sussed it out eventually...=D>

---

### Post by ekz13 on 2006-09-23
when I had the nvidia going, I had the onboard disabled, and eventually switched it back out for some reason while testing everything, that's ok though, I'm glad I finally got something to work... 

one more question though, how do you get new themes in Kubuntu.. there's no "get themes" button, wanted to switch out from the standard

---

