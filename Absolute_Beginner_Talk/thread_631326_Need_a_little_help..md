---
title: "Need a little help."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by circaender on 2007-12-04
so, i have burnt the graphic install .isos three times. The first time it loaded up and started to load up, the orange bar was going back and forth and then it glitched out and the bar was all over the screen and it stoped so i burnt it again...this time it loaded up and it just stoped mid way through...the third time it did what the first one did.. any ideas on how i can fix this? I really want to get this to work..

I have a

Intel Pentium 3.0 ghz
1 gig of ram
and a Nvidia Geforce FX 5500 graphics card

not the greatests..but from what i read should be more than enough to run Ubuntu, im just not sure what the problem is..

---

### Post by caravel on 2007-12-04
Try once more burning on the slowest speed.  Leave the PC alone while it's burning.  Reboot and boot from the cd and from the menu check the disc for errors instead of trying to boot straight off.

---

### Post by sethvath on 2007-12-04
Did you do a cd integrity check? 

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by rune0077 on 2007-12-04
Should be enough, yes. You problem might be that there was a glitch when you downloaded the .iso files. Try downloading them again and burn the new downloads.

---

### Post by Znort_Ubern00b on 2007-12-04
ignore me i'm stupid.(last comment deleted)

burn at slowest speed (x4) then check disc.

---

### Post by khgiese on 2007-12-04
I had a similar issue when I tried to boot off the Ubuntu 7.10 live CD on my home PC. The boot up screen seemed to go funky, with graphics getting all messed up. I thought the Live CD bootup was corrurpt and also did a couple re-burns. It appears that if I waited long enough on th eLive CD bootup that eventually I got the desk top. Not sure if this is what you are experiencing. I believe the Live Cd was having issues trying to resolve my Nvidia GX6800 video card.

---

### Post by circaender on 2007-12-04
ok, so i downloaded it again.. i burnt the iso, i checked for errors.. there were none. 
I tried loading it again, it looked like it was loading  and then after 15 or so seconds the graphics gost all messed up looking.. I let it sit there to see if the desk top would load eventually.. after about 10 minutes i turned my monitor off and then on and my monitor said 

Out of range

29.3khz/56Hz

i want to get ubuntu on my computer pretty bad..but im having a lot of trouble.

---

### Post by Dr Small on 2007-12-04
Alright, when it says that, try pressing CTRL + ALT + F1
And then enter this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by circaender on 2007-12-04
so, when it got to the screen and my monitor said out of range 29.2khz/56kh
I pressed Ctrl-Alt-F1 and a black screen came up and said loading..it loaded a list of things..
and had a little _ thing at the bottom, but would not let my type anything..

---

### Post by philinux on 2007-12-04
I'd try rebooting one more time but just leave it it can take ages, cos its a live cd. Once installed diff story.

You might need to alternate text based install.

---

### Post by circaender on 2007-12-04
> **philinux said:**
> I'd try rebooting one more time but just leave it it can take ages, cos its a live cd. Once installed diff story.

You might need to alternate text based install.

im not sure you have read through the thread, i sat there for 10 minutes with it looking all messed up and i turned off my monitor when i turned it back on it said out of range 29.2khz/56Hz.. 

im not sure waiting longer is going to help the above problem.....

and I dont really want to use the text based install, because if i can't get the live cd to load up..the same could happen with the real install..and then id have a bigger problem on my hands...

---

### Post by philinux on 2007-12-04
It takes 20 minutes on mine to get the desktop and yes I did read it twice.

---

### Post by circaender on 2007-12-04
okay..so i let it load for about an hour..and it still did nothing..still says  out of range.. 
I really wanted this to work..but i dont believe its going to...there is really no reason i should be having these problems..

---

### Post by sethvath on 2007-12-04
If you're using the livecd, get the alternate install disks.

---

### Post by philinux on 2007-12-04
Never tried it but click the 

Safe Graphics Mode.

It's probably the graphics card thats given it problems. Once installed it can be sorted.

---

### Post by circaender on 2007-12-04
okay, but what if it wont load after i install?
also.. i was reading someone else's post and they said they were having trouble with getting it to install on an HP.

mines a Gateway..could this have anything to do with it?

and also..and im sorry im so needy, whats the best way to install without getting rid of my windows? I plan on using only Ubuntu soon..but want to get to know Ubuntu/linux before i get rid of windows all together.

---

### Post by philinux on 2007-12-04
First thing is get the live cd up and running then you can see if you like it.

Some people dual boot on a single hard drive.

I dual boot with 2 HDD.

---

### Post by circaender on 2007-12-04
but i can not get the live cd running.. I have done everything that has been suggested.. most of the ideas i have done 2 to 3 times.. i have burned the .iso 5 different times, downloaded the .iso 2 different times.I checked the disk integrity and it said it was fine....i have waited on the load screen for an hour.. is it possible its just not possible for me?..

---

### Post by philinux on 2007-12-04
Ok,

1. Did you try the safe graphics mode.

2. What windoze operating system are you running now.

3. Have you got a windows install disk available and have you can you back up all your important stuff.

---

### Post by circaender on 2007-12-04
1) i tried the safe graphics mode last night..but that was with a disk i had not checked the integrity of..i can do that again.
2)Im running windows vista..but its the upgrade from xp
3)I dont think i have recovery disks..they didnt come with my computer..i can make some i think?
and ill back up all my pics/files.

---

