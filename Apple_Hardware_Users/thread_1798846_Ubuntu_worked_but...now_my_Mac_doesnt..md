---
title: "Ubuntu worked but...now my Mac doesnt."
date: 2011-07-06
forum: Apple Hardware Users
---

### Post by Saudude on 2011-07-06
Hello there,

I recently installed the newest version of Ubuntu on my PC and was amazed by it. Truly breathtaking. I then decided to try it out on my iMac with the Live CD. I thought it was a bit suspicious that after I restarted my Mac with the CD inside, it wouldn't boot it up. So me being the nublet I am, go into startup disk preferences and set the CD and restart. Ubuntu started up perfectly as expected, except for when I take the CD out. I literally can't boot into my Mac partition anymore. I tried pressing option when booting but alas, it gives me a lock and password entry (which not even my admin password works).

Please advise :(

---

### Post by snafu006 on 2011-07-06
**Resetting PRAM and NVRAM**

 
[LIST=1]
[*]Shut down the computer.
[*]Locate the following keys on the keyboard: Command, Option, P,  and R. You will need to hold these keys down simultaneously in step 4.
[*]Turn on the computer.
[*]Press and hold the Command-Option-P-R keys. You must press this key combination before the gray screen appears.
[*]Hold the keys down until the computer restarts and you hear the startup sound for the second time.
[*]Release the keys.
[/LIST]

In some cases, an Open Firmware-based computer may not respond to the  keyboard commands noted above, and may not allow starting up into Open  Firmware by pressing and holding the Command, Option, O, and F keys  during startup.  If you are unable to get to an Open Firmware prompt  (and your computer supports doing so), try powering on the computer with  the power button held down continuously—as if you were doing a firmware  update.  This should force the computer into Open Firmware, allowing  the steps in the article noted above to be used.

---

### Post by Saudude on 2011-07-07
> **snafu006 said:**
> **Resetting PRAM and NVRAM**

 
[LIST=1]
[*]Shut down the computer.
[*]Locate the following keys on the keyboard: Command, Option, P,  and R. You will need to hold these keys down simultaneously in step 4.
[*]Turn on the computer.
[*]Press and hold the Command-Option-P-R keys. You must press this key combination before the gray screen appears.
[*]Hold the keys down until the computer restarts and you hear the startup sound for the second time.
[*]Release the keys.
[/LIST]

In some cases, an Open Firmware-based computer may not respond to the  keyboard commands noted above, and may not allow starting up into Open  Firmware by pressing and holding the Command, Option, O, and F keys  during startup.  If you are unable to get to an Open Firmware prompt  (and your computer supports doing so), try powering on the computer with  the power button held down continuously&#8212;as if you were doing a firmware  update.  This should force the computer into Open Firmware, allowing  the steps in the article noted above to be used.

Thank you for your reply. I tried the methods mentioned above, however, no positive outcome whatsoever :(

Edit: Any way to perhaps change the boot priority on the Ubuntu Live CD?

---

### Post by B_Free on 2011-07-09
Do you have a Mac OS X disc? If you do, start up your computer, eject the disc, replace that disc with the Mac OS disc and restart. Open disc utility and choose your hard drive as the start up disc. You are set.

---

