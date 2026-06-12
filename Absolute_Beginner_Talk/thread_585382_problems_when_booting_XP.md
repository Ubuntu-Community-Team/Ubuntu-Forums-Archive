---
title: "problems when booting XP"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by thespankguy on 2007-10-21
i (finally) successfully dual boot windows xp and ubuntu 7.1. if i'm i ubuntu and restart the computer, then choose to boot xp, windows doesn't recognize my usb mouse. if i unplug it and plug it back in xp "finds new hardware" and it works fine. is there any way to prevent myself from having to unplug/replug it in everytime?

prior to the xp desktop showing up it also tries to run the "scandisk" type function to check my disk for errors and i have to stop it everytime.

---

### Post by Perpetual on 2007-10-21
Did your USB mouse work before installing Gutsy?  Also, did you let it do a complete scandisk or did you stop it each time it's tried to run?  Lastly, did you resize your XP partition when installing Gutsy?  If yes, did you do a couple defrags in XP prior to installing Gutsy?

It's been awhile but I am quite sure that if you resized your ntfs partition during installation, scandisk will run the first time you boot windows as the partition size has changed.  If you did not do a defrag prior to reisizing, you may have borked some of the windows files that were on the partition when you resized it.  If you have the windows disk, you might want to start over, install WinXP, defrag it, then do the Gutsy install.  Be sure to backup any important data on windows before you do the complete reinstall.

---

### Post by thespankguy on 2007-10-21
1. yes
2. i stop it, but i'll let it scan next time
3. yes
4. yes

i'm not going through all that again, i crashed a separate hard drive when installing gutsy the first time i tried, so i'm content with just unplugging it. i just thought maybe there was some sort of microsoft intellimouse explorer driver that i didn't have or something. thanks

---

### Post by Wiebelhaus on 2007-10-21
don't stop it , Windows has detected a file system error and is checking for any needed repairs , also stop hard booting and shut down properly.

---

### Post by mlentink on 2007-10-21
Quite frankly, I think this one needs quite a bit more data to diagnose correctly. I hear you saying you' re " content with just unplugging it" about Gutsy. Does this mean you installed it on a USB drive? Was the Windows drive connected at ll when you installed Ubuntu?

---

### Post by Perpetual on 2007-10-21
I think he meant he is unplugging the usb mouse, not a drive.

---

### Post by thespankguy on 2007-10-21
> **sx66gns said:**
> don't stop it , Windows has detected a file system error and is checking for any needed repairs , also stop hard booting and shut down properly.

i'll let it run next time, but how am i not shutting it down properly? i click the button, choose shut down or restart, when it boots the next time i choose windows xp...

> **mlentink said:**
> Quite frankly, I think this one needs quite a bit more data to diagnose correctly. I hear you saying you' re " content with just unplugging it" about Gutsy. Does this mean you installed it on a USB drive? Was the Windows drive connected at ll when you installed Ubuntu?

i mean the mouse

---

