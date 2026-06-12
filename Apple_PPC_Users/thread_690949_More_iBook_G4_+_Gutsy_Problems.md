---
title: "More iBook G4 + Gutsy Problems"
date: 2008-02-08
forum: Apple PPC Users
---

### Post by woojoo on 2008-02-08
Hello Ubuntu community,

Despite my love for OSX, I was persuaded by a friend to join the Ubuntu Revolution. I've attempted to install the system multiple times in the past, but failed to do so each time because of disk partitioning problems. When 7.10 Gutsy Gibbon PPC popped up on Digg, I decided to burn out old stack of CDs again. I'm a newbie at Unix, although I do know rudimentary Terminal commands (cd, ls, cp, nano). I own a 1.2Gh iBookG4 with a Radeon9200.

Here are the steps I've taken so far:

[LIST]
[*]I downloaded the image from here [(http://ubuntuforums.org/showthread.php?t=427714)]("http://ubuntuforums.org/showthread.php?t=427714") and burned it.
[*]Then I tried to boot it, but it blanked out with a black screen after the so called "busybox" (intramfs.)
[*]So I found this guide [(https://wiki.ubuntu.com/PowerPCKnownIssues)]("https://wiki.ubuntu.com/PowerPCKnownIssues") and followed it.
[*]It allowed me to boot the CD and install the OS on a guided continuous free space partition with no problems. 
[*]After the installation, I followed the guide and added "ide-core" to /etc/initramfs-tools/modules with the nano command and ran the commands ```
sudo update-initramfs -u 
```
[*]I then restarted and tried to boot into the new partition, but the screen blacked out the same way it did when I initially tried to boot from the CD. I suspected that the "ide-core" was appended to the "modules" in the wrong partition–the CD parition. 
[*]I booted from the CD again and added the same line of text "ide-core" to the new partition, which is labeled "disk" under /media/disk/etc/initramfs-tools/modules and again ran ```
sudo update-initramfs -u 
``` but yields the same result.
[/LIST]

So basically, I have Gutsy installed but cannot run it because of a busybox error. Does anyone have a solution?

---

### Post by calcioguy9 on 2008-02-08
I just installed Gutsy on my iBook G4 and had the same problems.  However, I tried the alternate install CD and everything worked easily.  I would try that!

---

### Post by woojoo on 2008-02-08
Would you please provide a link for me? I'm having a hard time finding the said file.

---

### Post by skier354 on 2008-02-08
here is the alternate cd link for gutsy [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

---

### Post by hrsetrdr on 2008-02-08
> **calcioguy9 said:**
> I just installed Gutsy on my iBook G4 and had the same problems.  However, I tried the alternate install CD and everything worked easily.  I would try that!

Good to know;  I had previously tried the desktop version on my ibook G3 but just got a blank display...forever.     I'd be happy to continue using  OS X 10.2.8 but it's not suitable for WPA wireless.

---

