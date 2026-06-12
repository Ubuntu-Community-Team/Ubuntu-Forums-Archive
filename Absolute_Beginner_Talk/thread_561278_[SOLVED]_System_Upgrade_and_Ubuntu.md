---
title: "[SOLVED] System Upgrade and Ubuntu"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Drevix on 2007-09-27
I had Ubuntu set up on my slave drive on my old P-III system, dual boot with WinXP on my master drive. The slave drive was dying so I copied everything over to a new drive, pulled it out and put it aside for the time being. I’ve since upgraded my system to a P-IV, basically transferred all my hardware over, including my master drive with WinXP on it. (Naturally, XP had to be a major pain but that’s all done). The master drive is as I left it when I was dual booting on my P-III, all I did was reset the MBR to Windows when it was on my old system. I plugged in the slave drive with Ubuntu on it on my P-IV, and can access the drive no problem, everything is there just as I left it.

Can I just reset my MBR to Linux control and boot up, or will Linux have a fit because of the different system it's on now? I’m hoping not to have to do a wipe and clean install, I don’t want to go through installing updates, various drivers, programs I’ve installed, and configuring various settings from scratch. But if there’s no other way, at least this time I’ll have a much better idea of what I’m doing and how to do it.

---

### Post by madoracle on 2007-09-27
You **might** be able to just add Linux to the MBR. Its worth a try at least, you can always change the MBR back to Windows only while figuring out if you'll need to reinstall Linux or not.

---

### Post by Drevix on 2007-09-27
I freaking hate Windows. If it weren't for a couple of expensive specialized programs I need to use I'd dump that sorry excuse for aggravating bloatware and never look back. It's sometimes hard to get over the differences between windows and Linux. Windows was a nightmare to get setup on my new system and took a good part of a day. I half expected Linux to do something similar. Well, I was wrong about that.

Linux, gee, plugged the hard drive in, booted up with my Supergrub disc, selected to boot up Linux. Booted up fine. Restored the MBR to Linux Grub. Done. Sorry it took so long.

---

