---
title: "Can I just start over?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by DXM31 on 2008-03-03
I tried to fix the wifi and lost the wired connection.
So I thought I could just reinstall but the partition screen is different than the last time, which was also different from the first time:confused:
If I boot off the cd I got wired but no wifi
If I boot off HD I get neither
I have an Acer with Atherso AR5007EG wifi card.
I also didn't realise(my fault) that Ubuntu was so hard to uninstall.
So like the title says, can I just start over? uninstall/reinstall
Thanks

---

### Post by Sinkingships7 on 2008-03-03
you shouldn't have any problems just reinstalling. just pop in the live cd and when it asks you the hard drive question, let it take over the whole HDD.

---

### Post by DXM31 on 2008-03-03
I still have Vista on there
Using dual boot
If I give Ubuntu the whole HDD wouldn't Vista be gone?

---

### Post by kplaxmaster on 2008-03-03
This is very strange.  If you have WiFi when you use the Live-CD, you should have it after the installation.

The only possible reason I could see is it being somehow linked to NetworkManager daemon.

To clarify matters, your goal is to not have to use the CD and to have wifi, correct?  You aren't updating any files after the initial installation as well, correct?  And you still have network manager enabled as it is by default?

Sorry for these tedious questions... just trying to grasp the problem at hand.  I will be watching this thread for a quick reply.  Hope I can be of service.

---

### Post by kplaxmaster on 2008-03-03
Yes, if you used Ubuntu to use the whole disk, you will over-write your Vista partition (unless you have multiple hard-drives, most likely not the case).  

Your error doesn't have anythign to do with dual-booting or vista luckily.  :guitar:

---

### Post by Sinkingships7 on 2008-03-03
> **DXM31 said:**
> 
If I give Ubuntu the whole HDD wouldn't Vista be gone?

yes it would. you're absolutely correct. what you'll want to do is select the manual option and partition the hard drive yourself so that you don't effect your vista partition. there are plenty of guides on how to do that on the internet. just search google and you should get some pretty promising howto's.

EDIT: an easier and faster way, which i forgot previously, is to boot off of your live cd and use gparted to resize your partitions.

---

### Post by DXM31 on 2008-03-03
> **kplaxmaster said:**
> This is very strange.  If you have WiFi when you use the Live-CD, you should have it after the installation.

The only possible reason I could see is it being somehow linked to NetworkManager daemon.

To clarify matters, your goal is to not have to use the CD and to have wifi, correct?  You aren't updating any files after the initial installation as well, correct?  And you still have network manager enabled as it is by default?

Sorry for these tedious questions... just trying to grasp the problem at hand.  I will be watching this thread for a quick reply.  Hope I can be of service.

I just have the wired connection with the CD, no wifi
My goal is to get Ubuntu to work with my wifi card and have a dual boot with vista
I am on vista now because I have the internet there.
Another issue is when Vista shuts down it take a looooong time since the install of Ubuntu.
Maybe that's normal for dual boot.

---

