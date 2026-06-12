---
title: "After install, boot hangs - problem = hard drive was IDE slave"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by bleair on 2007-06-24
On the slim chance anyone else uses such an unconventional setup and can't figure out why ubuntu won't boot

My computer has 1 hard drive and 1 cd-rom drive and I have been using it happily. I recently downloaded ubuntu to give it a try. I booted Ubuntu 7.04 as a live CD, tried out a few programs, liked what I saw and they performed the install. During the install I told the installer that it should format and use the entire disk.  Upon reboot the graphic boot screen would come up and then hang (no progress bar advance). Eventually I would get kicked back out to the busybox shell.

Of course there was no helpful error message or anything like that.

It turns out that my hard drive was in my machine as the IDE slave while my CD-rom drive was the master. Once I swapped master-slave assignments on the drives ubuntu booted up and all was good.

My google searches didn't point me to any documentation that listed this limitation, and a helpful warning from the installer or the boot program sure would have been nice... but anyway, I am now up and running. If you can't boot check your drives. Normally your computer's bios text messages will show the primary and master IDE channels and what drives are attached.

---

### Post by ronocdh on 2007-06-25
Many thanks for posting this, very good form. Hopefully someone will search and find this. For easy searching I know add some relevant tags:

Boot up failure boot screen hang progress bar freezes stops ide master slave

:KS

---

