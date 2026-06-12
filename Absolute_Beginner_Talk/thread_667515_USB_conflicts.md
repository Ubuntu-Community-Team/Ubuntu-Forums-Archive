---
title: "USB conflicts"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2008-01-14
Hi, I seem to have 3 somewhat incompatible usb devices.  Basically one is my logiteck webcam, which works fine.  Another is a Nova-t-500 usb pci card which when attached makes my usb webcam disappear, but otherwise appears to work.  And the third is another logitech device, a gamepad this time, which works fine if I plug it in once the computer is up and running, but if it's in at bootup then my remote control for the Nova-t-500 card gets messed up...

So as far as I can work out the problem is down to whats plugged in on boot up, but as all these devices work ok independently and even if plugged in together after boot up then the problem is becoming increasingly frustrating (especially as one is a pci card)...

please please help or point me in the right direction I really don't want to end up back in XP but the wife is nagging me to get it all working or else....

---

### Post by EnergySamus on 2008-01-14
Hmmm...

I have seen many issues of this type before. I don't know how to resolve it, but I do have somewhat good news for you! Even though you have Ubuntu installed, you can dual-boot it with XP or Vista.

Here is a link for dual-booting Ubuntu with XP:

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

And With Vista:

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)


Sorry that I couldn't resolve the issue, but dual- booting is a great thing. If you want to use Windows apps, you obviously boot into Windows!

Good Luck,
EnergySamus

---

### Post by Hightide on 2008-01-14
dual boot is a good a idea

I dont know if this will help but can you check if the cards are supported in ubuntu?

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

:)

---

### Post by vikram on 2008-01-14
Very hard to say what the issue could be. Have you tried monitoring the logs when you plug in USB devices ? this may offer a clue

tail -f /var/log/messages

---

### Post by EnergySamus on 2008-01-14
Most cards are supported in Ubuntu. I am not sure why his isn't working! :lolflag:

EnergySamus

---

### Post by db5007 on 2008-01-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/186453](https://bugs.launchpad.net/ubuntu/+bug/186453) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same problem. If I plugin any usb device at boot, it crashes and reboots. If I unplug it, wait for the system to boot up and then plug in the devices everything works fine.

I am running Ubuntu(7.10) 64bit on an Hp3200t slimline PC. 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00916910&cc=us&lc=en&dlc=en&product=3629378&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00916910&cc=us&lc=en&dlc=en&product=3629378&dlc=en&lang=en)

Does anyone have any advice on how best to trouble shoot the problem?

thanks in advance!

---

