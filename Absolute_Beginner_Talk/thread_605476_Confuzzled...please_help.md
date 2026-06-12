---
title: "Confuzzled...please help"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Sicklove on 2007-11-07
OK, here's the basic problem:

My girlfriend recently was given a PC by her brother, its pretty lame and runs Windows ME (;-;). She wants it just for browsing the web, but the performance was so bad that it was pretty unuseable. 

A work colleague suggested that Xubuntu might be a better OS. I downloaded the latest version yesterday (Gutsy Gibbon), and after trying it out on my work PC, took the CD home.

I inserted the CD and selected 'Start or Install' option. After sometime a desktop appeared with a number of icons for File System, Install etc. In fact it looked exactly how it did when i got it working on my works PC, the main difference is that the "Application Bar" was not appearing. I mean the one that goes along the top of the screen with the Applications menu and Quit buttons on.

No errors, just sorta sits there. 

I can give a basic rundown of the PC but some stuff i dont know so bear with me:

Manufacturer: IBM

Model: Netvista ??

Processor: AMD duron 

Memory: 128mb

Hard Disk: 9gb (5gb free)

Now after it failed, i returned to windows, ran scandisk, then defrag, then AVG scan.  This morning before i left for work i set it running again, hoping that the bar might have appeared before i get home, but i'm not confident.

I appreciate any suggestions, including ones that suggest i am perhaps just going to have to use Windows ME.

Many thanks ^^

---

### Post by TeaSwigger on 2007-11-07
Good news! You absolutely don't need to use the worst OS ever (IMH), Windows ME. There are many, far better options open to you.

Okay two things.

1) 128mb ram is awfully low. That's not enough to run a richly featured OS like Xubuntu in my opinion, and if it can you will have to use the Alternate Install CD (x86 Alternate), not the Live CD. 

2) It may be sharing that already awfully low 128mb ram with an integrated graphics card. If so, you pretty much have to look elsewhere.

My suggestions for what it's worth: 

1) Go get Puppy Linux. Burn it. Try it. If you don't like it or there's problems, keep it as a backup "rescue disk" because it can run the PC even if the installs mess up, and you can easily reformat and fix it.

2) If you do want a richer OS like Ubuntu, consider Fluxbuntu. It uses a "quirky" window manager called Fluxbox and file browser etc called ROX, but if you learn it, it's very customizeable and offers a good system that might be light enough to run nicely on that PC.

3) Consider adding more ram, bringing it to 384 at least, and you can run anything. Finding the right chip is tricky if you're unfamiliar but it's so easy to install - just push it in the slot, done. Then go with ubuntu, and let it use the whole disc and lose the Windows ME.  :)

Just some thoughts for you to consider. It'll just be trickier and require alternatives here and there, but you can do it. Enjoy and good luck :)

---

### Post by Doggles on 2007-11-07
How strange...

Here's a thought - maybe Xubuntu isn't detecting the graphics card or screen size properly? - sounds wierd, but maybe the top panel is there, just not visible because it's being displayed off the top of the screen? On your monitor, do you have an option to change vertical position?

If this is the case, then maybe use the alternate installer (test-based non-liveCD type) to install to the HD, then work on setting up graphics properly when you've got it installed (by opening a terminal and reconfiguring xorg.conf)

I suggest this one because when I installed Xubuntu Gutsy from the live CD, the fonts and menu bars looked all wierd, and some stuff appeared off-screen, but when I'd completed the install, everything sorted itself out.

Best of luck - Xubuntu seems nice and friendly when you do actually get it running, better than ME for what you want to do, so stick at it!

---

### Post by Sicklove on 2007-11-07
Thanks for the replies guys, i tried upgrading the memory, luckily i had an even older Compaq PC that had the same type of memory in it, before the ME machine was running on 64mb (lol). There was a 128mb card and a 64mb card in the Compaq, the 128mb one seemed to break the other PC so the 64MB had to do. 

The suggestion to check "off screen" for the menu bars is a good one, and i'll kick myself if that turns out to be the case. Im going to "borrow" a pc from work, and do the alternate install on the ME machine and just use the whole disk, if it breaks it, then she'll have to use the one i get from work to do her Facebook stuff on until i can buy a new one.

Thanks again guys, appreciate the fast responses.

All the best

Sicklove

---

### Post by Doggles on 2007-11-07
More than a pleasure mate - best of luck with this and don't forget to post back and let us know if you do get it working

---

### Post by RedSquirrel on 2007-11-07
> **Sicklove said:**
> I appreciate any suggestions, including ones that suggest i am perhaps just going to have to use Windows ME.

With only 128 MB RAM, you can't install using the Xubuntu LiveCD. You could try the alternate Xubuntu install CD, as suggested by TeaSwigger.

If Xubuntu is too slow, you might consider a minimal installation with Fluxbox or IceWM. IceWM is sort of Windows-like in appearance, so it might be an easier transition. I use Fluxbox, but it does take a bit of getting used to. ;)

You could also try the xfce4 metapackage with the minimal installation. Xubuntu uses Xfce, but in this case you'd be able to select your own packages and keep things light.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

