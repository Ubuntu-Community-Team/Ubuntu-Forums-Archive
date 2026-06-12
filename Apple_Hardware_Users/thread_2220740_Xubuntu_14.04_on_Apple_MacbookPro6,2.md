---
title: "Xubuntu 14.04 on Apple MacbookPro6,2"
date: 2014-04-29
forum: Apple Hardware Users
---

### Post by M1GEO on 2014-04-29
I recently upgraded from Xubuntu 13.10 to Xubuntu 14.04, since the upgrade banner had been splashing over my screen at boot.

However, since the upgrade, the machine has been a little bit unstable with regards to the graphics (wouldn't suspend on lid-close, or wouldn't resume properly).  I opted to select the recommended Nvidia driver.  Since this point, I am no longer able to get a login screen.  It boots to a black screen, and goes no further.  I can see all the kernel messages and nothing seems to look too crazy, there's no stack traces or anything dumped (that I can see) at boot.  If I use alt+ctrl+F1 (holding the Fn button to get F1 and not screen brightness), I can get a console login.

If there is a console way to fall back to the old open source driver that would be great.  People have suggested that installing the Nvidia driver from their site works, and if I can get some kind of graphics running again, I'll be able to experiment.  Unfortunately I'm currently in a public library with no install DVDs :(  The open source drivers are good enough for now, I'm just programming.

Thanks in advance.

George.

**EDIT #1**

So I got home and just completely reinstalled Xubuntu 14.04 from scratch.  It runs a lot nicer.  Instead of selecting the Nvidia driver from inside the Additional Devices dialogue, I used the driver from the Nvidia website.  It warned me it would disable the Nouveau driver with a file inserted within /etc/modprobe.d/.  After reboot the machine ended up in a state as above, black screen after boot. No luck.  It was easy to go into /etc/modprobe.d/ and remove the offending file, named something like "nvidia-installer-disable-nouveau.conf".  Reboot again and it worked.

I would however, like to run the proprietary driver such that the display buttons work and the machine suspends/resumes correctly.  Using the Additional Devices dialogue to install drivers leaves the system in a worse state where I cannot get in to remove the files.  Using the "init=/bin/sh" trick within grub, I was able to get a root shell, and also recover from this instance too.  Here, the Additional Devices dialogue install of the Nvidia drivers creates "nvidia-331-updates_hybrid.conf" and "nvidia-graphics-drivers.conf" (symlink).  Remove these and the graphics return to nouveau.

Looks like the nvidia driver is failing because of the Mac's EFI.  Great :(

---

### Post by M1GEO on 2014-07-07
This bug still plagues me on a daily basis.  Is there any known fix for this?

Any advice?

---

### Post by M1GEO on 2015-04-16
Has this been fixed yet. Struggled with this for over a year now... Driving me mad!

Is there a way to solve this issue?!

---

### Post by M1GEO on 2015-04-17
If anyone finds this thread, the Nouveau open source driver works much better on 15.04 beta. The brightness controls work, and the machine reliably wakes from standby.

---

### Post by Charlie_Harrison on 2016-03-15
Hi George, 

Thanks for persisting with your lonely posts into the wilderness!  I'm about to have a go at this myself.  [This post]("http://www.daybarr.com/blog/ubuntu-14-04-macbookpro6-2") seems to tackle similar issues to some of yours (certainly the brightness keys, and possibly the black screen issue).  I'll let you know if I have any success!

---

