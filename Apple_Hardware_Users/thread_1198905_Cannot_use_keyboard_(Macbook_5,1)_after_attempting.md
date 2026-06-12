---
title: "Cannot use keyboard (Macbook 5,1) after attempting touchpad fix"
date: 2009-06-28
forum: Apple Hardware Users
---

### Post by jermsie on 2009-06-28
I stuffed up while I was attempting to fix single and two finger soft-tap. This is what I was following:
```

A workaround is to run sudo gedit /etc/modprobe.d/blacklist.conf and add

**blacklist usbhid**

then run sudo gedit /etc/modules and add

bcm5974
usbhid

This will make sure that the modules are loaded in the appropriate order. 

```

The problem is... I only added "blacklist usbhid" and then got distracted.
On reboot, the touchpad is a bit slow and I can't type anything to fix my blunder.

Using Ubuntu 9.04

Help? :)

---

### Post by dman777 on 2009-06-28
boot up with a rescue disk. then mount the root partition. chroot into it and you'll be able make changes.

---

### Post by jermsie on 2009-06-28
> **dman777 said:**
> boot up with a rescue disk. then mount the root partition. chroot into it and you'll be able make changes.

Could you maybe elaborate on that?

So do I run the livecd? What do I do from there

---

### Post by jermsie on 2009-06-28
> **dman777 said:**
> boot up with a rescue disk. then mount the root partition. chroot into it and you'll be able make changes.

Solved.
As dman777 suggested: 
I booted the livecd, went into text-mode and selected recovery.
Manually mounted the drive and navigated to the file I needed to change.
Done.

---

### Post by dman777 on 2009-06-28
glad it worked. i couldn't help you to much becuase i use gentoo instead of ubuntu. but fundamentally, all linux sys are the same(for the most part).

---

