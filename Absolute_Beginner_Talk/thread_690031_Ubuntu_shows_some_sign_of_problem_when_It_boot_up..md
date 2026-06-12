---
title: "Ubuntu shows some sign of problem when It boot up."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-07
Hi
Thank you for reading my post
I tried to use Hibernate feature of Ubuntu but it was not similar to windows hibernate, it just bring back a login screen. I tried the suspend feature and it was the same.

After some minutes I restart my computer and OMG, it shows a black screen with an small red message in the left bottom corner : "NO ACTIVE PARTITION" When I saw this I dead from the amount of fear that it inject into my mental system.

but happily I pressed the Enter button and it showed the GRUB boot loader. and It can boot the linux normally.

problem is that every time that I restart the computer I should see the same killing message, and then I can press enter to see GRUB boot loader ....

Can some one please let me know:
1-what does it means?
2-how much serious it can be?
3-how I can backup my boot? partition and reuse it later if anything goes wrong?

Thank you.

---

### Post by talsemgeest on 2008-02-07
Take a look here: [http://en.opensuse.org/SDB:BIOS_notifies:_NO_ACTIVE_PARTITION_FOUND](http://en.opensuse.org/SDB:BIOS_notifies:_NO_ACTIVE_PARTITION_FOUND)

Hope this helps:)

---

### Post by dcstar on 2008-02-07
> **legolas_w said:**
> Hi
Thank you for reading my post
I tried to use Hibernate feature of Ubuntu but it was not similar to windows hibernate, it just bring back a login screen. I tried the suspend feature and it was the same.

After some minutes I restart my computer and OMG, it shows a black screen with an small red message in the left bottom corner : "NO ACTIVE PARTITION" When I saw this I dead from the amount of fear that it inject into my mental system.
..........

Unplug any USB drives out of your system when you boot, or change your BIOS so the PC doesn't try to boot off USB devices.

---

