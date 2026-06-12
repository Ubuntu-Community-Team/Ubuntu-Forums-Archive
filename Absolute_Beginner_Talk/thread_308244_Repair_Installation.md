---
title: "Repair Installation"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-11-27
On the live CD for 6.06, where can i find the repair installation option? i have corrupted my network settings, and need to repair it, anyhelp? (I cannot afford to un-install, or do anything that will loose settings, hence why i want the repair feature :))

---

### Post by bionnaki on 2006-11-27
first menu upon bootup

---

### Post by Captain Kirk76 on 2006-11-27
You sure, it only says install/start ubuntu and check CD for Defects. (as i said, i don't want to INSTALL just REPAIR a previous installation)

---

### Post by turbojugend_gr on 2006-11-27
Hmm, I can't understand, how can you re-isntall ubuntu in a way it will only override the network settings while all other settings will be left in tact. IMHO it's not possible to only repair network settings using the LiveCD, if the settings are to be changed that means, you have to format you root "/", so all other settings will be lost, exept those stored in your HOME (which btw are the vast majority-but are not system configs, just apps configs etc) provided you will keep your /home partition (if any) unformatted.

Long story short, you can't just overide networks settings using a reinstall function., all _system_ settings will be reset to defaults. Thus I would advice you to let us know of your problem and try helping you fix it.

Best Reagrds, TJ.

P.S: Could someone affirm waht I am saying, just in case I remember sth the wrong way.

---

### Post by juantovarm on 2006-11-27
Does the live cd have a repair opton? never seen it. I have seen it on the alternate install disk. I have tried it once, but i guess i did something wrong cause it didn't do me much good ](*,)

---

### Post by Captain Kirk76 on 2006-11-27
well my problem is this

less /etc/network/interfaces/ - No such file or directory
less /etc/resolv.conf - No such file or directory

I somehow deleted those files, which screwed my network up, so i need them replacing with the default (the default workd for me) so i need to re-install. the internet works on the LiveCD thogh :D, but not practical for long term use)

Any hlp?

---

### Post by turbojugend_gr on 2006-11-27
Well those files are not defaults actually, they are created during your boot of the LiveCD, so try copying those from a LIVECD session to a usb stick or sth, and then putting them on your installed ubuntu, I can't see a reson this won't work, so give it a try.

---

