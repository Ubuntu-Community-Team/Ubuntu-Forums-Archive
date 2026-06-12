---
title: "MacMini 3,1 + BT keyboard/mouse"
date: 2009-03-21
forum: Apple Hardware Users
---

### Post by hajk on 2009-03-21
Should we start a thread on this?

Let me just summarize my own experience so far with the new (2009) 2.0GHz MacMini + small BT aluminum keyboard + BT mighty mouse, based on trying three distros: Ubuntu Intrepid, Debian Squeeze, and Ubuntu Jaunty (Alpha-6):

1. Restarting (hot rebooting) from either of these distros or their respective installers freezes the computer. The same holds when restarting from the rEFIt menu. The Mac Mini must be shut down (cold reboot) instead.

2. BT keyboard and mouse are available as simulated USB HID devices, both during installation and after booting the installed distros. The mouse scroll ball does not work in HID mode, however. Keyboard and mouse can be switched to HCI mode, though, and that fixes the scroll ball issue. 

3. The fn-key on the keyboard does not work in either HID or HCI mode. Toggling /sys/module/hid/parameters/pb_fnmode (older kernels) or /sys/module/hid_apple/parameters/fnmode (newer kernels) between 1 and 2 has no effect. So, no Delete and Page Up/Down functionality. Curiously, the Eject button works (complete with on-screen pictorial) when the applesmc module is loaded. 

4. There are only two frequencies known to acpi_cpufreq, 1.60GHz and 2.00GHz, so that the Mac Mini will still run hot even when "idling". I can't imagine that Intel would design a modern C2D processor with only two P-states... 

5. Broadcom 4328 wireless, for which the Broadcom hybrid "wl" driver works.

6. Suspend/hibernate works fine, using power button to return. Own fan setting in /sys/devices/platform/applesmc.768/fan_min1 is lost after returning from susp/hib.
 
Everything else seems to work pretty well when following the various Ubuntu and Debian MacIntel wikis.

---

### Post by justdave72 on 2009-04-03
Can you tell me how you got the BT keyboard/mouse working at all?  I can't get it working on mine, either in Intrepid or Jaunty.

I filed [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/344559](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/344559) on it a few weeks back.

---

### Post by hajk on 2009-04-03
Well, the BT keyboard/mouse are available at boot time as simulated USB devices, the Apple firmware takes care of that. 
You can check that this is true by running the "sudo lsusb -v" command. Unfortunately, the fn-key on the keyboard and the 
trackball on the mouse don't work this way -- that requires reconfiguring these devices as real Bluetooth ones. Of course, 
the BT packages "bluetooth", "bluez-utils" and "bluez-gnome" must be installed for this.

First step, keyboard/mouse must be unpaired in Mac OS X: just remove them in the Preferences -> Bluetooth panel. It helps 
to have temporary wired USB keyboard/mouse attached... ;)

Second, reboot into Ubuntu (with wired keyboard/mouse still attached), and disable the BT keyboard/mouse with```

$ sudo hciconfig hci0 reset
```

Third, in Jaunty (Beta) make sure that the Bluetooth applet works, then (using the wired keyboard/mouse) use the applet to 
scan for new BT devices -- this will find the BT keyboard/mouse and pair them (just use "0000"), after which you can 
disconnect the temporary wired keyboard/mouse.

The fn-key on the BT keyboard now works and the keys F10-12 will work with sound; and the scroll ball on the mouse works as well.

Unfortunately, these pairings don't survive a reboot, not even when adding the line```

options hci_usb reset=1
```to a file like /etc/modprobe.d/options.conf. I consider this the real bug.

---

### Post by cooloney on 2009-04-26
> **hajk said:**
> 

Unfortunately, these pairings don't survive a reboot, not even when adding the line```

options hci_usb reset=1
```to a file like /etc/modprobe.d/options.conf. I consider this the real bug.

hci_usb module was replaced by btusb module, so please try this ```
 options btusb reset=1 
``` to /etc/modprobe.d/options.

I tested on my MBP 5,1 with Jaunty, it will survive on reboot. Very cool.

-Bryan

---

