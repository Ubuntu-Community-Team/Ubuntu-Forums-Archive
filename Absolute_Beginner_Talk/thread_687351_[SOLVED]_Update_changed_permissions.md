---
title: "[SOLVED] Update changed permissions"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Just_this_guy on 2008-02-04
I have just bought a new laptop with Ubuntu 7.04 (FF) installed.  It was working fine until just recently.  As expected, there were a lot of updates due, so this morning I installed them and restarted.  Now I find that a) the laptop will not connect to my Wi-Fi, so I have no Internet access, and b) when I tried to enter a new appointment on Evolution it told me that I had selected a read-only calendar.

I am guessing that the update has changed some permissions, which would explain the Evolution problem and perhaps the Wi-Fi one.

Is there a smart way to recover the lost functionality?

By the way, many years ago I used to use Unix on the command line, but I have been a Windows luser for a long time now, so you'll have to speak gently.

---

### Post by Cypher on 2008-02-04
After the update were there additional Ubuntu options added to your GRUB boot menu? If so, perhaps the Kernel that was pre-installed for you (with WiFi support) was overwritten by a newer generic version that probably doesn't have that support.

If this is the case, you should be able to boot into the older Kernel and get your WiFi running and also "pin" the Kernel package to the one that works for you so that the updater doesn't try to update that package.

I'm a little lost on why any update should cause your personal files to be modified in your home directory.

So start with a terminal (Applications->Accessories->Terminal) and try
```

cd .evolution
ls -la

```
and let's see what files and permissions you have..

---

### Post by Just_this_guy on 2008-02-04
> **Cypher said:**
> After the update were there additional Ubuntu options added to your GRUB boot menu? If so, perhaps the Kernel that was pre-installed for you (with WiFi support) was overwritten by a newer generic version that probably doesn't have that support.

If this is the case, you should be able to boot into the older Kernel and get your WiFi running and also "pin" the Kernel package to the one that works for you so that the updater doesn't try to update that package.

I'm a little lost on why any update should cause your personal files to be modified in your home directory.

So start with a terminal (Applications->Accessories->Terminal) and try
```

cd .evolution
ls -la

```
and let's see what files and permissions you have..

Thanks
I listed the .evolution directory as you suggest and all the files seem to have user rw (or rwx) permissions.  Maybe it isn't a permission problem, but it does look like one.  The message from Evolution says:

Cannot create a new event
You have a read-only calendar source selected. Change to Calendar View and highlight a calendar that can accept appointments.

How do I boot into the older kernel and do the "pinning" as you suggest?

---

### Post by Just_this_guy on 2008-02-04
I was fiddling around trying to get the Wi-Fi to work and I entered System -- Administration -- Network.
The window showed the wireless connection enabled.  In desperation, I disabled it, by unchecking the box, and then enabled it by checking the box again.  That shouldn't do anything, right?  But blow me, it thought about it for a bit and then the Wi-Fi light on the laptop stopped flashing and came on continuously.  I opened Firefox, and lo and behold it worked!

That doesn't solve the Evolution problem, but that's less urgent.

---

