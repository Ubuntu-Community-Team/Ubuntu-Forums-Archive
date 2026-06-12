---
title: "Help! Complete Beginner!"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by bechardl on 2007-11-02
I just downloaded Ubuntu onto my computer last night, I had Windows XP.  Now I can't get my wireless internet to work at all.  I have tried 1000 things that the internet keeps suggesting and its getting me no where.  I hear it may be because my wireless card doesn't support Linux, but I don't evne know how to find what wireless card i am using! I need some serious help, please.

---

### Post by rudeboyskunk on 2007-11-02
If the wireless card came pre-installed, go to the computer vendor's website (e.g., HP, Dell, NEC), and look for your computer and find its specifications.  If not, try System>Preferences>Hardware Information and look for it there.

Linux may very well not support your wireless card.  But if that's the case, you can always try ndiswrapper using the Windows driver.

---

### Post by bingoUV on 2007-11-02
> **bechardl said:**
> I just downloaded Ubuntu onto my computer last night, I had Windows XP.  Now I can't get my wireless internet to work at all.  I have tried 1000 things that the internet keeps suggesting and its getting me no where.  I hear it may be because my wireless card doesn't support Linux, but I don't evne know how to find what wireless card i am using! I need some serious help, please.

Is it a laptop, or a branded desktop? If so, please post the model. If you have forgotten, try hard to find it (payment receipt, original packing etc). Also, search the internet with linux, <model number> ,wireless. You will get better results.

Open a terminal, and run the command
```

lspci

```

Post the output of this command here. This might help us figure out the wireless hardware used on your machine.

---

### Post by isparkes on 2007-11-02
Can you post some more information about your predicament:

 - Are you seeing any wireless networks at all, or is it that you are unable to use the wireless card?

- Do you see any network icon next to the clock on the upper panel near the clock? Does it have a yellow warning symbol?

 - If you are unable to use the wireless card, what is it? Can you find out what it is in XP in the hardware list in the control panel?

I'm sure that someone here will be able to help you out, but we're going to need some more to work with...

Fingers crossed.

---

### Post by bechardl on 2007-11-02
i'm not sure if this is right.  I have Vendor: Broadcom corporation
Device: BCM4318 [Airforce One 54g] 8802.11g Wireless LAN Controller
This is the only thing I can find that says wireless on it???

---

### Post by rudeboyskunk on 2007-11-02
There's your problem.

Broadcom is a bitch when releasing info about its hardware to the public.  Can hardly make any Linux drivers for it.

You'll probably have to use ndiswrapper.  Search the Ubuntu forum for an "ndiswrapper howto" and you'll be able to find a way.

---

### Post by isparkes on 2007-11-02
This might help:

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by bechardl on 2007-11-02
thanks :)

---

### Post by soaklord on 2007-11-02
I believe this is the exact same card I have.  You need to go here:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

And you will be up and running wirelessly shortly.  Good luck!!!

---

### Post by bechardl on 2007-11-02
Ok wait.  I went to the thread suggested, and starting doing everything it told me to.  however, once I typed in 
sudo apt-get install ndiswrapper-utils
and then typed in my password
it gave me a huge problem
Package ndiswrapper-utils is not available but is referred to by another package
this may mean that the package is missing, has been disabled, or is only available from another source
however, the following packages replace it:
ndiswrapper-common
e: package ndiswrapper-utils has no installation candidate




what do i do now???

---

### Post by Maestro23 on 2007-11-02
> **bechardl said:**
> Ok wait.  I went to the thread suggested, and starting doing everything it told me to.  however, once I typed in 
sudo apt-get install ndiswrapper-utils
and then typed in my password
it gave me a huge problem
Package ndiswrapper-utils is not available but is referred to by another package
this may mean that the package is missing, has been disabled, or is only available from another source
however, the following packages replace it:
ndiswrapper-common
e: package ndiswrapper-utils has no installation candidate




what do i do now???

Need to enable all your repositories.

System>>Admin>>Software Sources.

Make sure all sources are checked. Universe/Multiverse, etc...

Then try your ndiswrapper install.

---

### Post by bechardl on 2007-11-02
I should check everything off in all of the tabs????

---

### Post by Maestro23 on 2007-11-02
> **bechardl said:**
> I should check everything off in all of the tabs????

Check everything on the 1st tab.

---

### Post by bechardl on 2007-11-02
So I went in and checked the sources, tried again and it gave me the same problem.... is there a way to temporarily switch back to windows to  be able to download neededthings onto my computer... some of these threads are saying ... now download this and it gives me a link but im on a different laptop than the one that has linux to get information on how to fix my laptop with linux on it.... im soooo confused

---

### Post by soaklord on 2007-11-02
OK, just to make sure...  You aren't trying to install this stuff with NO internet connection are you?  I had to connect to my router through a cable to download and install everything, then configure the wireless card so I had wireless connectivity.  So, take a network cable and attach it to the laptop and the router, you will be MUCH happier than trying to use two different computers.  Once you have connectivity, and you know you can get to the internet, try the above post/posts directions again.

---

### Post by mdpalow on 2007-11-02
You should install a fresh copy of 7.10 again onto your laptop and this time make sure you are connected to the Internet VIA an Ethernet cable (CAT5). When it installs, it will connect to the Internet to grab some more installation files. 7.10 is working with Broadcom wireless, so I'm thinking you just need to have a cable plugged into your laptop the first time. I'm suggesting the re-install 'cause it sounds like you've been installing and changing a lot of things based on other advice. Might want to just have a clean copy loaded at this point. You already know how to install, so the whole process shouldn't take more than about 12 or so minutes. I think you'll have success if you re-install with cable plugged in. After install, then you can unplug cable and set-up wireless. Let us know how it goes...

---

