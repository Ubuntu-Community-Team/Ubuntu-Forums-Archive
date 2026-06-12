---
title: "iMac G5 wireless/driver issues!"
date: 2009-07-19
forum: Apple Hardware Users
---

### Post by ibu on 2009-07-19
I pulled the trigger and decided to switch to Ubuntu on my old iMac G5 (Ambient light sensor model, no iSight) with a 1.8ghz processor and 768mb of ram, in hopes of making it just a bit less sluggish than it was when it was running Tiger.

I downloaded and installed the alternative PPC disk (because I read that some people had better luck with it) for Jaunty 9.04. The OS installed just fine, however, when I go to System > Administration > Hardware Drivers, it doesn't detect any drivers.

So, I don't have wireless working which is a huge problem! I tried [this]("https://wiki.ubuntu.com/PowerPCFAQ#Will%20my%20wireless%20work?"), but it didn't work. It wouldn't find the driver when I typed the command in inside of Terminal.

I can't hook this computer up to a wired connection because of where it is in the house. Is there anything I can do?

I have some other issues, like sleep/wake not working (when I click hibernate, the screen goes black but with the backlight on, and fans turn up all the way which is very loud, and I can't "wake" out of that). However, I would like to get this wireless issue addressed first because then I can actually use the system.

Thanks in advance!


EDIT: I managed to connect this iMac via Ethernet and internet works fine. I've reinstalled the system using the regular desktop cd (before, I was using the alternate CD) and now the Broadcam driver shows up under System > Administration > Hardware Drivers. I've installed & activated the driver, restarted, but Ubuntu still fails to connect to any wireless network, it doesn't pick up any networks in range to connect to and even when I select "Connect to hidden wireless network", it still won't connect to anything. =/

---

### Post by roym4 on 2009-07-28
We've tried on many iMac G5s and have also been unable to get wireless (airport extreme) working, even after installing b43-fwcutter. Works fine on G4 iMacs and g#/G4 powerbook/ibooks.

---

