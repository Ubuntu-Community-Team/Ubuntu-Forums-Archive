---
title: "BCM4306 Drivers on Compaq R4000 using Ubuntu 6.1"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Greyhaven7 on 2007-03-20
Hello Everyone,
Here's the story:
I've had the Vista beta running on my system for several months now, and it's finally pissed me off to no end. While I used to love Windows, Vista has shown me that Microsoft has no earthly clue how to build a stable operating system. SO, I'm taking my laptop, formatting it, and dual booting into Ubuntu 6.1 and Win2KPro. 

The Ubuntu install went flawlessly. I'm now in the system and all seems well. However, I don't have access to the internet. Here's the rundown:

OS: Ubuntu 6.1 (AMD 64 version) -  Downloaded last night from the front page of Ubuntu's site. Correct me if I'm wrong but this is a 64bit version of Ubuntu, right?

Comp: Compaq Persario R4000 (laptop)

WLAN card: onboard Broadcom BCM4306

LAN card: onboard Realtek RTL-8139 (/....C and /....C+)

Situation: Computer SEES both of the cards and can identify them. It just can't seem to USE them. I haven't been able to find anything on the Realtek card, and my focus was primarily on the WLAN since I'd much rather have that one working. 

Since Broadcom apparently sucks and didn't release drivers for Linux, I'm trying to run them through ndiswrapper. So I've run through the steps, putting ndiswrapper on my desktop, typing in the sudo commands, etc... everything seems to be going well untill... I get an error that says:

> WE HAVE DETECTED THAT YOU ARE USING EDGY EFT WITH AN
********
*INCOMPATIBLE* *64BIT* *KERNEL*
********
Please read: 
http://<<there's a link here but I can't access it since I don't have the internet>>
This is a bug, and a bug report has already been filed. 
Aborting...please rerun after the problem is fixed. 

So, I'm assuming that means that the win kernel it's trying to run in ndiswrapper isn't 64bit and therefore is not working within the 64bit version of Ubuntu, correct? 

So, what do I do to get to the interent? I keep coming up short on solutions for the BCM4306 including one forum post that said:
> If it's a BCM4306, good luck! A lot of banging your head into walls...
I'm new to linux and I don't want to get disheartened, someone please help. 
If you need more info on my system, etc... please let me know.

---

### Post by srt4play on 2007-03-20
My advice is to reinstall with the regular Desktop installation cd.  

You will save yourself a lot of time and stress overall.

---

### Post by Greyhaven7 on 2007-03-20
But I just installed with the regular desktop installation CD (downloaded, burned and installed last night). I haven't done anything since then, just try to get the network card working. 

Is there anything else I can do? 

Will reinstalling fix anything (do you think it was a bad install or something)?

---

### Post by srt4play on 2007-03-20
What I meant was the regular desktop cd, as in not the AMD64 version but the 32-bit i386 version.  There are some things (ndiswrapper being one of them if I remember correctly) that will be more difficult to set up in 64-bit and for a new user it will just make life that much easier going with the i386 cd.

---

