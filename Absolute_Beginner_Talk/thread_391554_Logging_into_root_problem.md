---
title: "Logging into root problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by MikeyRibbs on 2007-03-23
Okay, my external harddrive now works but I can't write any files to it because it is read only. I think I need to log into root to change it so that I can write to it. When I try to log into root it says root logins allowed. I have kde installed but I'm mainly using ubuntu. The KDE login shows up and I and choose ubuntu. So how can I login to root or is there a way I can do it in my user account.

---

### Post by taurus on 2007-03-23
What format is that external harddrive?  If it's ntfs, then you need to install ntfs-3g first before you can write to it.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by justleen on 2007-03-23
You wouldnt need to logon as root really.
If you need root-right, just use sudo in terminal
(or, as HymntoLife pointed me out, use sudo -i, that will gave you a "root" session)

---

### Post by MikeyRibbs on 2007-03-23
Ok, I did that but now when I  click on it to open the drive it says," Opening "External" You can stop this operation by clicking cancel."
But it doesn't open? Any help?

---

### Post by taurus on 2007-03-23
Did you mount your external harddrive and how did you mount it?

---

### Post by MikeyRibbs on 2007-03-23
No, how do I mount it?

---

### Post by MikeyRibbs on 2007-03-24
How do I mount, help please.

---

### Post by taurus on 2007-03-24
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by MikeyRibbs on 2007-03-24
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
michael@michael-desktop:~$

---

### Post by taurus on 2007-03-24
You have a SATA drive and that's where Ubuntu is installed!  What exactly are you trying to do?  Are you trying to modify stuff outside $HOME?  If that's the case, then you need to use either sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by macogw on 2007-03-24
> **MikeyRibbs said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
michael@michael-desktop:~$

There's only one hard drive listed.  Do you have the external plugged in?  Do that command with it plugged in.

---

### Post by MikeyRibbs on 2007-03-24
No i have an external also, how do i use it!?

---

### Post by macogw on 2007-03-24
Is Ubuntu on both of them or just the internal one?

---

### Post by MikeyRibbs on 2007-03-25
Just the internal.

---

### Post by eljalill on 2007-03-25
Well, you could plug the external in and type in a terminal
```
fdisk -l  /dev/sdb 
```
and put the output here.

If it doesn't let you try the same with sudo in front.

---

