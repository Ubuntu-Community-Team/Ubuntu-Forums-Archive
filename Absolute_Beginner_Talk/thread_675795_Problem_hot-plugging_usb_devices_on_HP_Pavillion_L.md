---
title: "Problem hot-plugging usb devices on HP Pavillion Laptop"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by metafractal on 2008-01-23
Hi,
I am running Ubuntu Gutsy 64-bit on an HP Pavillion dv9000 laptop with AMD Turion X2 64 Processor.  If I boot with usb devices plugged in, Ubuntu recognizes them fine, but if I plug in the devices (usb mouse, mp3 player, flash drive) after booting, they are not recognized.

I have checked that "Mount removable drives on hot-plugging" is checked under "Removable Drives and Media."

This is the output of lsusb when I boot with devices plugged in:

Bus 002 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04e8:5080 Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000  

This is the output of lsusb when I plug in devices after booting:
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000 

I believe the "62c0 Microdia" is the inbuilt webcam.

Any help would be appreciated!

---

### Post by cdtech on 2008-01-23
This sounds like a "USB Daemon" issue.

I'm just throwing something out there for ya. You didn't roll your own kernel did you?

The only supported "USB Daemon" is enabled by a kernel configuration option (CONFIG_HOTPLUG), The more modular your kernel USB configuration is, the more initialization needs to be done in scripts after the kernel starts to run. Hal is one such app. Try this in terminal:

```
 sudo /etc/init.d/hal restart
```

You should get " * Restarting Hardware abstraction layer hald"

could be that its not started at boot time, so check your proper rc directory.  

I hope this helps.

---

### Post by metafractal on 2008-01-23
Thanks for your reply but I'm still getting the same problem. I ran sudo etc/init.d/hal restart and got "Restarting Hardware abstraction layer hald." Sound Juicer popped up, recognizing the audio CD I had in the drive, but the USB devices were still not recognized (I tried running the command both before and after the devices were plugged in).

I did not compile my own kernel, in fact this is a practically clean install and I have done very little fiddling around with it.

What is my proper rc directory?

Cheers,
meta

P.S. For the record, the same USB ports work fine under Windows Vista, so we can rule out it being a hardware problem.

---

### Post by cdtech on 2008-01-24
You can find your proper rc directory by using the command..

```
runlevel
```

should be something like
N 2 - which means /etc/rc2.d directory.

[ATTACH]57351[/ATTACH]
What ever you have in this directory that has an "S" at the beginning is started on boot. Anything that starts with a "K" is not loaded at boot.

You need to make sure that users allowed to mount removable devices are listed in the "plugdev" group...

```
usermod -a -G plugdev <username>
```

If that doesn't work for you, look in /usr/share/hal/fdi/policy/ and see if there is a file with the extension .fdi . If you have a program close with an error it's known to leave it in this directory. The solution is to simply open that program and close it again (with the same user that opened it before). The file should remove itself.

---

### Post by metafractal on 2008-01-24
Now this is really strange... the USB drive has started working, but only occasionally. I thought it was fixed, because I booted up twice and all USB devices were mounting perfectly. The third time I booted, no devices will mount.

I located my proper rc directory and checked that hal was being started at boot-time (it was). Here is an output of my rc directory:
```
README                       S20apport         S30gdm
S05vbesave                   S20hotkey-setup   S89anacron
S10acpid                     S20makedev        S89atd
S10powernowd.early           S20nvidia-kernel  S89cron
S10sysklogd                  S20powernowd      S98usplash
S10xserver-xorg-input-wacom  S20rsync          S99acpi-support
S11klogd                     S22consolekit     S99laptop-mode
S12dbus                      S24avahi-daemon   S99rc.local
S12hal                       S24dhcdbd         S99rmnologin
S19cupsys                    S25bluetooth      S99stop-readahead

```

I tried sudo usermod -a -G plugdev josh; it is not clear whether it worked or not - like I said, it worked one boot, not the next.

Have you any idea what's going on?

---

### Post by cdtech on 2008-01-24
Hey metafractal, did you get your problem solved?

Did you get a chance to look in the:

```
/usr/share/hal/fdi/policy/
```

and see if you had a file with the extension .fdi ?

If a program shuts down improper such as gparted (so I've heard) it leaves this file in that directory.
Just by opening the program and closing it proper will correct the problem. I know, sounds weird but it does work.

Some say by deleting that directory ( /usr/share/hal ) and reinstalling hal corrects the problem, but by doing that you delete some files that are not replenished by the re-install.

So by finding the application thats blocking hal from working properly is the best method.

---

### Post by metafractal on 2008-01-25
First of all, thanks so much for all your help!

I have looked at /usr/share/hal/fdi/policy/. The folder contains two folders (10osvendor and 20thirdparty) and nothing else. 20thridparty is empty; 10osvendor contains a number of fdi files. Here is the directory listing of  /usr/share/hal/fdi/policy/10osvendor/ :
```

10-cpufreq.fdi
10-hal_lpadmin.fdi
10-keyboard-policy.fdi
10-laptop-panel-mgmt-policy.fdi
10-macbook-backlight.fdi
10-macbookpro-utils.fdi
10-power-mgmt-policy.fdi
10-rfkill-switch.fdi
10-usbcsr-mice.fdi
15-storage-luks.fdi
20-storage-methods.fdi
debian-storage-policy-ignore-fixed-crypto-drives.fdi

```

I'm not sure what this means though... which program should I open and close?

---

### Post by cdtech on 2008-01-25
None, if there are no files in the root of the policy folder then your ok. Wow, I'm kinda lost now. So it did work for a time..hmmmm.

I just intercepted this thread, I think this may help you. [[COLOR="DarkRed"]usb[/COLOR]]("http://ubuntuforums.org/showthread.php?t=674334")

Good Luck.....

---

