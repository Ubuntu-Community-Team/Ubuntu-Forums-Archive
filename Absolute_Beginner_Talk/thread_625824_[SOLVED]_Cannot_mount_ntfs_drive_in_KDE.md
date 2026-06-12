---
title: "[SOLVED] Cannot mount ntfs drive in KDE"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by liviubero on 2007-11-28
Hello, I use Ubuntu 7.10 and I wanted to give KDE a try, so I installed kde-core and kdm.
 I have an external ntfs hard disk drive and I can read and write it with no problems in Gnome (ntfs-3g installed). But when I change to KDE, I keep receiving
 > hal-storage-removable-mount-all-options refused uid 1000 when I try to open it.
 If I change back to Gnome, then the drive is all right.
 I do have on the internal drive a ntfs partition and that one I can read and write with no problems. Only when I try to read the external drive, it doesn't work.
 Does someone have any idea?

---

### Post by vikram on 2007-11-28
I'm not an expert but this seems like a permission issue unrelated to the desktop environment.  have you tried going to the Konsole and mounting the drive manually and reading the drive as normal user and as root (using sudo ?)

> **liviubero said:**
> Hello, I use Ubuntu 7.10 and I wanted to give KDE a try, so I installed kde-core and kdm.
 I have an external ntfs hard disk drive and I can read and write it with no problems in Gnome (ntfs-3g installed). But when I change to KDE, I keep receiving
  when I try to open it.
 If I change back to Gnome, then the drive is all right.
 I do have on the internal drive a ntfs partition and that one I can read and write with no problems. Only when I try to read the external drive, it doesn't work.
 Does someone have any idea?

---

### Post by _sAm_ on 2007-11-28
Have you installed and tried the NTFS Configuration Tool, you will find it in Synaptic. I had to use it myself on an external drive in ntfs.

---

### Post by liviubero on 2007-11-29
> **vikram said:**
> have you tried going to the Konsole and mounting the drive manually and reading the drive as normal user and as root (using sudo ?)
I don't know how to mount manually a drive.
> **_sAm_ said:**
> Have you installed and tried the NTFS Configuration Tool, you will find it in Synaptic. I had to use it myself on an external drive in ntfs.
Yes, in the configuration tool the check box for writing external drives is checked.
Once more: in Gnome, there is no problem with reading and writing the drive. Only when I login in KDE.

---

### Post by FuturePilot on 2007-11-29
Try this.
```
sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
```
```
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```
Then try mounting it.
There's a bug here
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768")

---

### Post by KhaaL on 2007-11-29
I've had this problem, it's kinda annoying but very easily fixed.

Go in to the storage media, right click on the partition/device and select properties, in one of the tabs there is a checkbox that gives you the option to mount it as a user... uncheck that and voila! :)

---

### Post by liviubero on 2007-11-29
> **KhaaL said:**
> I've had this problem, it's kinda annoying but very easily fixed.

Go in to the storage media, right click on the partition/device and select properties, in one of the tabs there is a checkbox that gives you the option to mount it as a user... uncheck that and voila! :)

Wow!
It worked!
Thanks for that.

---

### Post by DO55 on 2008-01-29
> **KhaaL said:**
> I've had this problem, it's kinda annoying but very easily fixed.

Go in to the storage media, right click on the partition/device and select properties, in one of the tabs there is a checkbox that gives you the option to mount it as a user... uncheck that and voila! :)

thanks

---

