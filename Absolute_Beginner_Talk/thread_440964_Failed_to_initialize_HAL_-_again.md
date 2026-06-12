---
title: "Failed to initialize HAL - again"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by netsoul on 2007-05-12
Hi guys,

I know that this topic was discussed over here, but it seems that my case is a bit different. 

Yesterday, I installed all updates suggested by the update manager and HAL was among it. Now, when I try to boot GNOM I got this message: "Failed to initialize HAL" .  AS a result, all my network adapters disappeared (including laptop's WiFI).

I want to point out that it happened **right after I installed latest HAL updates **and rebooted.

Do you know how to fix that problem?

Thanks.

---

### Post by ucsblaw on 2007-06-18
i have the exact same problem and its driving me nuts...any suggestions..anyone?

---

### Post by ububaba on 2007-06-18
> **ucsblaw said:**
> i have the exact same problem and its driving me nuts...any suggestions..anyone?

Count me in.

---

### Post by ucsblaw on 2007-06-18
this problem sucks...big time...i don't even have internet connection with feisty so i can try and solve the HAL problem...I keep having to reboot to XP and write everything i find out by hand.

I was thinking...I think the problem occured after i updated my computer and had new versions of HAL installed. Is there anyway I could force downgrade HAL to what it was before without internet connection? Would I be able to use a live CD to do this? I am lost here...this is the 2nd time an update has screwed up my perfectly working ubuntu....im going to stop updating from now on.

---

### Post by aktiwers on 2007-06-18
Its a bug...  I had the same problem.. there is a solution that works for some here:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

I ended up doing a reinstall though.

---

### Post by ucsblaw on 2007-06-19
> **aktiwers said:**
> Its a bug...  I had the same problem.. there is a solution that works for some here:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

I ended up doing a reinstall though.

I tried everything on that site and nothing seems to work...thanks again for trying.

Anyone else?

How about rolling back to the old HAL from a live CD? Is that possible?

---

