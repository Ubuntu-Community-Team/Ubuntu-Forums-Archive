---
title: "Installing on MBP, stuck on boot"
date: 2013-01-21
forum: Apple Hardware Users
---

### Post by sneike on 2013-01-21
Hi all, I was installing Ubuntu 12.04 on my MacBook Pro (model 5,3).. I made the partition with Disk Utility (16GB of free space) and I prepared an USB stick using [this guide]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick").. using rEFIt I boot with the USB until the Ubuntu’s boot menu, but when i choose the option "try ubuntu", it gets stuck with the black screen and the flashing white underscore..

so actually i can't move on, but i can't neither go back, because disk utility doesn't recognize anymore the free space partition that i created..

please, any help is appreciated..
thanks
DNL

---

### Post by sneike on 2013-01-22
i solved the previous issue using a live cd instead of the usb memory flash..

so i correctly installed the OS but unfortunately now i have another issue. when i choose to boot with ubuntu from the grub screen, i get stuck with these error codes:

```
[8.417978] [drm] nouveau 0000:02:00.0: DCB I2C entry invalid
[8.516004] [drm] nouveau 0000:02:00.0: PRAMIN flush timeout
[12,455571] [drm] nouveau 0000:02:00.0: PRAMIN flush timeout
[16.328490] [drm] nouveau 0000:02:00.0: PRAMIN flush timeout
```

in [this thread]("http://ubuntuforums.org/showthread.php?t=1648279") i found this solution
> After completing the installer, Ubuntu still wouldn't boot- in recovery mode, I'd see a "pramin flush timeout" error message, which was related to problems with the builtin nouveau nvidia driver. By adding "nouveau.noaccel=1 blacklist=vga16fb" to the kernel boot options, I was able to get past that error and boot, then fix the problem permanently by installing the proprietary nvidia driver
but i can't figure out how to make it work.. i tried to modify the boot option with grub, but it doesn't boot yet.. 

any advice?

thank you
DNL

---

### Post by sneike on 2013-01-23
i found a workaround to bypass the above issue.. with grub i choose the recovery mode, and when prompted i choose to resume the normal boot..

a popup appears saying: [I]You are now going to exit the recovery mode and continue the boot  sequence. Please note that some graphic drivers require a full boot and  so will fail when resuming from recovery. If that's the case, simply  reboot from the login screen and then perform a standard boot.

[/I]if i restart again performing a standard boot i still have the same problem.. is there a way to solve it definitely now from inside ubuntu? do i have to change something about the graphic drivers?

thanks for your help

---

