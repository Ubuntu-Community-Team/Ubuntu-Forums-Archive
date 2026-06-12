---
title: "What GNU/Linux distributive works on macbook air A1466?"
date: 2013-01-10
forum: Apple Hardware Users
---

### Post by I_K on 2013-01-10
Can anyone using macbook air A1466, please, tell me the version of GNU/Linux distribution it works fine with?

Thank you in advance!

---

### Post by powerpcliberation on 2013-01-10
I have no experience with running Linux on a MBA but I can tell you from other experience that it generally doesn't play as nice on over-engineered Apple hardware.  That means systems like the MBA, iMacs etc. don't run it as well without a massive amount of configuration.  Systems that heavily modify hardware standards to suit the case/enclosure design and put that before hardware function.  Because of this it is heavily engineered to run Mac OS.  The best way to run other OS is in a virtual machine.  That will be a lot less of a headache for you.

For booting Linux as the main OS a Mac Mini or Mac Pro will generally make a good Linux system.  Older PowerPC systems like G4 towers are perfect Linux machines.  Everything always works out of the box.  You can pick them up for $50 and under on Craigslist and Ebay.

Just my two cents.

---

### Post by I_K on 2013-01-10
powerpcliberation, thanks a lot for your post and suggestions!

I would like to try MBA though.

---

### Post by webfiend on 2013-01-15
It's generally true that Apple's hardware starts getting cranky as soon as you try running non-Apple operating systems on it. However, I have been running Ubuntu 12.10 on my MacBookAir5,2 with minimal issues. It actually runs more smoothly for me than Windows 8, which I have not been able to get past the post-install stage.

The only issue I had with Ubuntu 12.10 was with wifi. Initially it uses the wl module, but that just goes away after the first update. A smarter geek would probably take the time and figure out how to fix that, but I just loaded the alternative "brcmsmac" module with `[FONT="Courier New"]sudo modprobe brcmsmac[/FONT]` in Terminal. That got wifi back on, so I added brcmsmac to */etc/modules* to ensure that it loaded on next reboot.

It works well for me as a development machine. I have not tested its gaming capabilities, because that usage is not a priority for me.

Have fun!

---

