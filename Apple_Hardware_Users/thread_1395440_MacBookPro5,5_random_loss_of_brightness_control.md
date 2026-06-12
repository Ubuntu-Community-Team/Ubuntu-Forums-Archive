---
title: "MacBookPro5,5 random loss of brightness control"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by DizzyTech on 2010-01-31
My MacBookPro5,5 (also known as the June 2009 Unibody MBP) is having brightness problems.  Usually, with OOTB Ubuntu, I can control the brightness flawlessly with the keyboard keys labeled F1 and F2 with no problems once I install the nvidia_bl driver.  Pommed improves the experience, giving me keyboard brightness.  

Since installing yesterday, the brightness control randomly stopped working.  Xev reports that the brightness up and down keys return a keycode (whereas F7 - F12, the playback and volume keys do not; both sets control their respective stuff natively)... this shouldn't happen.  nvidia_bl is loading properly according to dmesg; so this problem is baffling.

The Gnome brightness applet does not work, nor does auto dimming.  The applet displays a helpfully-apt red circle-with-slash mark.  "echo x | sudo tee -a /sys/class/backlight/nvidia_backlight/brightness" still works to change the brightness manually.  I can get the Gnome brightness working by manually changing the brightness, killing gnome-power-daemon, and then restarting it via the terminal in no-daemon mode.

Any ideas?  Solutions?  Suggestions?  This is the one thing not working flawlessly with my MacBook Pro under Ubuntu (yes, I even got standby working!) and it's *infuriating* to somebody as obsessive as me.  Any help is appreciated!

---

### Post by WindPower on 2010-02-02
I have exactly the same problem with a Macbook Pro 5-3 since the recent nvidia-bl-dkms update (version 0.15.1). I'll try to downgrade and report the results soon (if I figure out how to do that...)

---

### Post by DizzyTech on 2010-02-02
Sorry to peel the thread out from under you, WindPower, but I'm gonna mark it as resolved.  The update actually fixed things for me after I removed and reinstalled the package.  I also realized that I had changed the "model" of my keyboard in Keyboard Layouts to "MacBook Pro", though the default 105-keyboard layout included support for all system and FN keys (save for the keyboard backlight ones) using the XF86 key names.  Now, if only I could get the keyboard illumination working without pommed... that would be great!  :D

---

### Post by WindPower on 2010-02-02
I downgraded to version 0.15 by downloading it [straight off Launchpad](https://launchpad.net/~mactel-support/+archive/ppa/+builds?build_text=nvidia-bl-dkms&build_state=all) and installed with sudo dpkg -i path/to/downloaded/package.deb
Shutdown and turned on again, and this time the screen was recognized and I could adjust the screen brightness slider that appeared on-screen, but the screen itself didn't change its brightness at all.
Then I uninstalled nvidia-bl-dmks and mbp-nvidia-bl-dkms, shutdown, start again, installed nvidia-bl-dkms=0.15 and mbp-nvidia-bl-dkms (latest), shtudown, start again, and I'm still back to square two (the brightness slider can be moved but it has no effect on the actual backlight).

This is especially infuriating due to Ubuntu's already mediocre battery life (50% of OS X's battery life for me, despite all the hacks I've tried in this forum), because a screen stuck to the maximum brightness sucks that battery life even faster. :(

But reported here: [https://bugs.launchpad.net/mactel-support/+bug/516354](https://bugs.launchpad.net/mactel-support/+bug/516354)

---

### Post by WindPower on 2010-02-02
> **DizzyTech said:**
> Sorry to peel the thread out from under you, WindPower, but I'm gonna mark it as resolved.  The update actually fixed things for me after I removed and reinstalled the package.  I also realized that I had changed the "model" of my keyboard in Keyboard Layouts to "MacBook Pro", though the default 105-keyboard layout included support for all system and FN keys (save for the keyboard backlight ones) using the XF86 key names.  Now, if only I could get the keyboard illumination working without pommed... that would be great!  :D

Well good for you I guess... Could you remove the solved tag and change the title to Macbook Pro 5-3? That'd prevent me from creating another thread for that... I'm kind of fed up with all the reboots I did and all.

---

### Post by DizzyTech on 2010-02-02
Yes, I'd be glad to.  I highly recommend *removing* mbp-nvidia-bl-dkms, as it's only ever caused problems for me.  In fact, remove both, reboot, and then install only the latest nvidia-bl-dkms.  That's what worked for me.  (I had the same problems as you, identically!)

---

### Post by WindPower on 2010-02-03
> **DizzyTech said:**
> Yes, I'd be glad to.  I highly recommend *removing* mbp-nvidia-bl-dkms, as it's only ever caused problems for me.  In fact, remove both, reboot, and then install only the latest nvidia-bl-dkms.  That's what worked for me.  (I had the same problems as you, identically!)Sadly that changed nothing. ](*,)

---

### Post by _mario_ on 2010-02-04
> **WindPower said:**
> I downgraded to version 0.15 by downloading it [straight off Launchpad](https://launchpad.net/~mactel-support/+archive/ppa/+builds?build_text=nvidia-bl-dkms&build_state=all) and installed with sudo dpkg -i path/to/downloaded/package.deb
Shutdown and turned on again, and this time the screen was recognized and I could adjust the screen brightness slider that appeared on-screen, but the screen itself didn't change its brightness at all.
Then I uninstalled nvidia-bl-dmks and mbp-nvidia-bl-dkms, shutdown, start again, installed nvidia-bl-dkms=0.15 and mbp-nvidia-bl-dkms (latest), shtudown, start again, and I'm still back to square two (the brightness slider can be moved but it has no effect on the actual backlight).


this might be somewhat my fault. i finally managed to get auto-loading to work using the former blacklist as whitelist. but due to a lack of information this doesn't seem to be perfect. i specifically need the following information:
```

$ cat /sys/class/dmi/id/product_name
$ lspci -nn

```
of the following models: MacBook Pro 5,1 through MacBook Pro 5,5. and does the machine incorporate one or two graphics adapters?

second: you shouldn't install both drivers. that's why nvidia-bl-dkms blacklists mbp-nvidia-bl-dkms as of version 0.15.1.

thanks & ciao,
Mario

---

### Post by buntuLo on 2010-02-04
> **_mario_ said:**
> i specifically need the following information:
```
$ cat /sys/class/dmi/id/product_name
$ lspci -nn
```
of the following models: MacBook Pro 5,1 through MacBook Pro 5,5. and does the machine incorporate one or two graphics adapters?
MBP5,1 has two graphics adapters (9400m and 9600mgt).
```
lo@malamela:~$ cat /sys/class/dmi/id/product_name
MacBookPro5,1
lo@malamela:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b2)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.4 RAM memory [0500]: nVidia Corporation Device [10de:0a98] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
00:0b.0 IDE interface [0101]: nVidia Corporation MCP79 SATA Controller [10de:0ab5] (rev b1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac4] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9600M GT] [10de:0647] (rev a1)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
05:00.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW643 PCI Express1394b Controller (PHY/Link) [11c1:5901] (rev 06)
```

---

