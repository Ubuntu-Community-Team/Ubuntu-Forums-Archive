---
title: "Intel Mac Mini soft reset boot issue"
date: 2007-05-26
forum: Apple Intel Users
---

### Post by nocarrier on 2007-05-26
hello all,

i did a fresh install of Ubuntu 7.04 not dual-booting.  if I reboot from the gnome menu, I get a black screen on boot and the monitor shuts off.  if I power cycle the machine, it boots fine directly into Ubuntu... any ideas?

(sorry if this has been answered, but I have been reading all about this and never saw this problem specifically)

---

### Post by ronocdh on 2007-05-28
> **nocarrier said:**
> hello all,

i did a fresh install of Ubuntu 7.04 not dual-booting.  if I reboot from the gnome menu, I get a black screen on boot and the monitor shuts off.  if I power cycle the machine, it boots fine directly into Ubuntu... any ideas?

(sorry if this has been answered, but I have been reading all about this and never saw this problem specifically)
I haven't seen this before either, but I'm curious (and extremely friendly, also, awesome) so I'm giving it a bump. You mean that you are doing a hard shutdown, i.e. holding the power button till it clicks off, yes? I know that there are issues with installing Feisty solo (no dual boot) because Ubuntu is used to BIOS/MBR setups instead of GPT/EFI ones. 

I cannot understand how this would affect your soft/hard rebooting. Perhaps post search through the other forums for posts on GNOME rebooting not working? You may get a lot of people shoving you to the Apple Intel forums if you posts, but it'd be interesting to find out whether it's a hardware independent issue....

---

### Post by iCara on 2007-05-31
Hi guys,

same problem here.

A friend sold me a used Intel MacMini, without hardware defects.

It had OSX and winxp (bleah) in dual boot with bootcamp.

I inserted Feisty x86 32bit CD, live version loaded smoothly and i installed with option "erase and use all disk".

Ubuntu is working fine as usual, but i have this reboot problem.

When i "sudo reboot" or "Gnome reboot" system powers off correctly but freezes on new boot.

If i go for "sudo halt" and then push the power on button all works fine.

This is a great problem with remote control: i cannot reboot or i would lose it.

I do not know if it is something related to bootcamp (do not know if Ubuntu installation deleted it or not, by default).

I used to see a folder with a question mark on applegrey screen when booting and then Grub loading. After a p-ram reset (apple+alt+p+r) i do not see that ? anymore, but problem remains.

Any ideas?

Thanks,
r.

---

### Post by entangled on 2007-05-31
Don't know if this is relevant to you but I get instant monitor sleep and no grub boot on my Intel Mac Mini if I have a live USB DVD writer with no boot media. It may happen with flash memory too.
My system is direct dual boot - Macosx on the first GPT partition, Ubuntu on second MBR partition and boot camp allows me to choose, as long as I unplug my USB drive. But I can boot off the USB as long as it contains bootable media.

---

### Post by iCara on 2007-06-01
It can be somehow related...i have a usb webcam plugged in and it has a little power on during boot.

I have also usb keyboard and mouse...the *strange* thing here is that if i move mouse and press keys while display is grey reboot correctly goes to Grub (and does not freeze with monitor that powers off).

---

### Post by ggreco on 2007-06-11
Look also at [this post]("http://ubuntuforums.org/showthread.php?t=467958")

I've NOTHING connected to the mini except the monitor and the network cable, 4 times out of 5 the mini doesn't soft reboot... I've tried both with the .15 and the .16 2.6.20 images.

No luck and no hints till now...

---

