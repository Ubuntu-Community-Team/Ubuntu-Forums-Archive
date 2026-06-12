---
title: "System pauses or hangs at startup (Dell E1505 running 6.10)"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by meuge on 2007-04-10
Hi

I am loving Ubuntu, however I have an issue I need some help with. My Dell E1505 laptop's wifi card was recognized and configured by Ubuntu just fine. The laptop has a killswitch that allows the card to be turned on/off using a keyboard shortcut. 

However, when the killswitch is set to "off", the system will either boot fine and quickly, or will hang at the loading screen, about 40% into the progress indicator. 

When the killswitch is set to "on", the system boots fine, but it pauses at about 40% of the progress indicator for 1-2 minutes, while the wifi status light blinks, then continues loading without a problem. 

Has anyone encountered this issue, or has a solution? Thanks...

---

### Post by rbprogrammer on 2007-04-10
i have the same laptop with the same problem (based on your description)...

but what i had to do was log in, as hard as that was, then issue the following command:
```
sudo tune2fs -c **1** /dev/hda1
```

i'm not sure why... but this command makes it so that it checks your filesystem where the OS was installed.  mine was installed on hda1, so you may need to change that depending on your partitions.

again, not sure why this worked, but now i boot up perfectly every time. **but**, it does take a minute or two longer to boot up. but to me, at least i get to boot up

---

