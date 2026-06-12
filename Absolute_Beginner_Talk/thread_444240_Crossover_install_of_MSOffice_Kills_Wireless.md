---
title: "Crossover install of MSOffice Kills Wireless"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-15
Ok, so, I spent the weekend hooked up to my wired connection working to get my wireless adapter to work via ndiswrapper - must have re-installed 7.04 25 times in the process.  The good news is that I got it working.  The bad news is that, having come back to my remote office where there is no wired connection, I re-downloaded Crossover and installed MSOffice XP.  That install routine installed Explorer 5, not in a bottle, but on my desktop.

Now, I can't say for certain that the culprit is Explorer 5, but, the next time I tried to start Ubuntu, it went into some sort of recovery mode at the point where network drivers (for my wireless) would have been loading - that point where the little light on my wireless normally starts blinking.

There was a bunch of code on the screen - checking this-ok, that-ok, networking-no ok or anything.

Machine hung there for quite a while, and then the screen just went blank.

Restarted the computer and Ubuntu loaded, but the dialogue box where I normally can see that the driver for my N1 is installed is totally blank, hangs, and I get a message that it is not responding - Wait or Force Quit.

If I go into 'Network', my wired connection shows, but the wireless connection is no longer showing up.

Now, I know I can re-install Ubuntu to set everything right (argh!!), but, I'm guessing that a successful re-installation to restore my wireless adapter is not possible without a working internet connection (right, or am I wrong?).

So, other than a fresh install, is there a way to recover/repair that wireless adapter/restore the drivers and/or ndiswrapper without a live internet connection?

Does anyone else have experience with Explorer (or perhaps some other component of WinOfficeXP) breaking the wireless setup?

Would uninstalling Explorer fix things?

And, lastly, is there a way to install MSOfficeXP via Crossover without polluting my system with Explorer - divorcing myself from various versions of that noxious ap was one of my motivations for moving to Ubuntu in the first place.

Thanks for any replies/suggestions.

Caruso

---

### Post by dstew on 2007-05-15
All good questions. You can try to restore your system without re-installing by using the recovery mode option. It gets you a command-line interface, and you can try to figure out what is going wrong. After you boot, you can look at the messages from the loading modules using the command **dmesg**.

---

### Post by carusoswi on 2007-05-15
I tried recovery mode (will try it again, I guess).  The boot up stalled at the same point - something about loading network or checking network connections or something like that.  I discovered this problem because a boot up stalled and flipped into the recovery mode screen when I had not selected recovery mode from the grub menu.

The only reason I'd like to be able to fix this now is that I will have no internet access without that adapter until I can get the computer back to my home this weekend.

Ubuntu without the internet is like "the spring without the fall" as they say in the pancakes jingle.

Thanks for the reply.

Caruso

---

### Post by dstew on 2007-05-15
One more thing to try. Uplug the network adapter, boot, shut down, plug in again, boot. Other than that, I don't have any more idea. I have no experience with Crossover. Sorry.

---

### Post by carusoswi on 2007-05-16
> **dstew said:**
> One more thing to try. Uplug the network adapter, boot, shut down, plug in again, boot. Other than that, I don't have any more idea. I have no experience with Crossover. Sorry.

Thanks for the suggestion - it did not work.  Ndiswrapper is not to be found on my system since installing MS Office for whatever reason.  Obviously, that install broke something, and I believe IE to be the culprit.  MS is forever requiring this or that to be installed - I hate IE . . . oh, well, I have some other suggestions to try - if they don't work, I'll just play chess or something until this weekend.

Caruso

---

### Post by carusoswi on 2007-05-27
FWIW, I never did get this sorted out, but, brought the computer home and wired it to my router, reinstalled Ubuntu, installed Automatix, then, NDIS Wrapper, and all is almost well - I can now use iwconfig to get the adapter assorted with any router that I discover (including my own).  And, of course, NDISWrapper is newly and (I believe) correctly installed on my system.

An answer as to why I cannot get WEP security to work continues to elude me, so, I just disabled broadcasting of my ESSID on my router to provide some small measure of security.

Don't know if that is the final answer or not, but it's the best I can do for now.

Caruso

---

