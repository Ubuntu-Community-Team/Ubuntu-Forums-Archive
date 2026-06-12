---
title: "PowerBook G4 Titanium - Modem setup?"
date: 2005-05-24
forum: Apple PPC Users
---

### Post by TDave on 2005-05-24
Hi all

Apologies if this has already been covered, but I tried a quick scan through the forums and couldn't find it - currently out in Egypt with an extremely slow and delicate internet connection, so thought I'd go straight for the quickest response!

A while back I installed Ubuntu (4.10) on my PowerBook G4. Obviously, I'm not expecting the AirPort Extreme to work (except in my dreams), and I know the ethernet port worked fine, but I was wondering if anyone experienced problems with the modem?

When I went into network settings to set it up I didn't notice any problem, however when I came today to actually TRY and get it working I came across the problem of it not connecting.
Firstly, I tried to connect by opening the Network Settings and checking 'active' next to the configuration. Two seconds lettter the checked box becomes unchecked, hence not active. Trying to configure it and autoconfiguring simply details that it can't be detected (the default was to /dev/modem).

Unfortunately I haven't had time to play with it right now as the electricity generator fails on me shortly, so I will play with it more the next few days until I next get to try it.

Anyone have any ideas as to what it would be? Any reported/known issues? I haven't heard of any but it could be possible I missed it.

Sorry if this seems quite vague, newbie status is pretty high and definite, I can assure you.

Thanks a lot.

Dave

---

### Post by DJ_Max on 2005-05-24
Here's some reference, [http://ubuntuppc.info/CompatibleMachines/PowerbookG4Titanium15inch1GHz](http://ubuntuppc.info/CompatibleMachines/PowerbookG4Titanium15inch1GHz)

I don't know what modem the Titanium uses, the installer probably didn't detect the modem, therefore couldn't set the drivers in the kernel. Find the modem brand, and you can then compile a custom kernel.

---

### Post by shaneo on 2005-06-25
If you wait (about 3 min after clicking on the activate box) it will start to dial up.
Ubuntu will take about 3mins to initialise most modems. 

ShaneO'

---

