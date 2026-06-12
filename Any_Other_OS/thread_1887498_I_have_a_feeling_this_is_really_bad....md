---
title: "I have a feeling this is really bad..."
date: 2011-11-27
forum: Any Other OS
---

### Post by doppel.ganger on 2011-11-27
Whatever this is, is it fixable? Did a reboot, same thing.

---

### Post by navaleshubham10 on 2011-11-27
are u using recoverable mode?

---

### Post by doppel.ganger on 2011-11-27
Nope, just a regular boot.

---

### Post by Elfy on 2011-11-27
Thread moved to Other OS/Distro Talk.

---

### Post by cgroza on 2011-11-27
Maybe running fsck will fix it.

---

### Post by doppel.ganger on 2011-11-27
How do I do that?

---

### Post by 3rdalbum on 2011-11-27
Boot from a live CD (an Ubuntu one, or the Fedora live CD image, or any Linux live CD).

Find out the device file name of your Fedora partition by running:

```
fdisk -l
```

as root (if you're using an Ubuntu live CD, do "sudo fdisk -l" instead).

When you find the device file name, that starts with /dev/ that corresponds with your Fedora partition, just run:

```
sudo fdisk (device-file)
```

So, for instance, "sudo fdisk /dev/sda1" if your Fedora partition is /dev/sda1.

---

### Post by doppel.ganger on 2011-11-27
OK! I'll try that! Thanks!

---

### Post by ajgreeny on 2011-11-27
> **3rdalbum said:**
> Boot from a live CD (an Ubuntu one, or the Fedora live CD image, or any Linux live CD).

Find out the device file name of your Fedora partition by running:

```
fdisk -l
```as root (if you're using an Ubuntu live CD, do "sudo fdisk -l" instead).

When you find the device file name, that starts with /dev/ that corresponds with your Fedora partition, just run:

```
sudo fdisk (device-file)
```So, for instance, "sudo fdisk /dev/sda1" if your Fedora partition is /dev/sda1.
That should really be ```
sudo e2fsck /dev/sdx#
```I think you got fdisk muddled up with fsck; it's fsck that does the file check and hopefully repair needed, not fdisk.

---

### Post by doppel.ganger on 2011-11-27
So,
```
sudo fdisk -l
``` for the fist and ```
sudo e2fsck /dev/nameofdevice
``` for the second?

---

### Post by doppel.ganger on 2011-11-27
Hmmmm.... Loading slower than usual.

---

### Post by doppel.ganger on 2011-11-27
OK, Now I'm really concerned. I boot up, which takes longer than usual. I press F12 to enter Startup Disk selection. [I]My plugged in Fedora 16 USB is not there!

---

### Post by LinuxFan999 on 2011-11-27
> **doppel.ganger said:**
> OK, Now I'm really concerned. I boot up, which takes longer than usual. I press F12 to enter Startup Disk selection. [I]My plugged in Fedora 16 USB is not there!
Is your USB stick recognized when it is plugged into a different computer ?

---

