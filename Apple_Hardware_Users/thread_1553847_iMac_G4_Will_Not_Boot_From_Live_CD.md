---
title: "iMac G4 Will Not Boot From Live CD"
date: 2010-08-15
forum: Apple Hardware Users
---

### Post by drewdlephone on 2010-08-15
Hey gang. I presently have an iMac G4/700Mhz machine I want to try Ubuntu on, but I cannot get it to boot using the 10.04 PPC Live CD. I get to the boot prompt, and no matter what I type, the system halts when the screen clears and comes up, and each time it does so, it comes up different colors (I've seen green, red, yellow, and grey so far). I've tried the special boot arguments that apply to this system when you press the TAB key, and all of them end the same way, so I'm at a wee bit of a loss here. 

Thanks for any help.

---

### Post by teejmya on 2010-08-16
I remember these days... 
When I ran Ubuntu on my iBook G4, (7.10 I think it was...) I had to boot the live cd with -nosplash -powerpc -quiet
Or something near that. Check the list of usable kernels with the tab key, and see if any of those match up.

Let me know how it goes.
Good luck.

---

### Post by drewdlephone on 2010-08-19
I'll try those suggestions, as well as anything else I can find. If I cannot boot the system with any of the options, is there another way forward or am I stuck?

EDIT: No luck with any of the prompt options.

---

### Post by linuxopjemac on 2010-08-19
do an alternate installation (not GUI). We can make X work after that.

---

### Post by drewdlephone on 2010-08-30
Okay, will try that and let you know how it goes.

---

### Post by drewdlephone on 2010-08-31
Awesome! I'm looking at the non-GUI installer working it's magic right now. All that was needed was to type install-ppc at the Yaboot prompt, which didn't work on the regular disc.

---

