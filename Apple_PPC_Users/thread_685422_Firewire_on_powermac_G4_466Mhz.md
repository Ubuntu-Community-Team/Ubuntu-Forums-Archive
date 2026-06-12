---
title: "Firewire on powermac G4 466Mhz"
date: 2008-02-02
forum: Apple PPC Users
---

### Post by Rizado on 2008-02-02
Hello,

I've had a external firewire drive connected to a PowerMac G4 and everything was working fine untill sometime this summer, after I got home from holiday it just didn't work anymore. I figured the firewire ports were broken as the drive worked using usb and on other computers. However a few days ago the harddrive crashed so I started running from a old feisty live cd instead (The computer is used as a router) and suddenly the firewire drive works again?

I think I might have updated the kernel before or after the holidays and that might just have been when the drive stopped working. So I guess this is a kernel bug? Anyone else who have had the same problem?

---

### Post by stream303 on 2008-02-02
I've found firewire drives to be somewhat cranky and only relegate them to being OSX drives.  The code doesn't seem robust enough for me to trust it with anything else.  Sometimes firewire drives can be misconfigured as ethernet devices, "ethernet over firewire".  Sometimes even OSX fails.

I've been bitten by that works-for-months-then-fails syndrome more than I care. :)

Can you live with an external usb-drive as a simple data-drive,  even though your model is only usb 1.1 compliant?

---

### Post by stmiller on 2008-02-03
Firewire has been under heavy development in the Linux kernel over the past couple of major kernel releases. Depending on what firewire controller is on the external drive box, you may have good or bad luck. 

Update to the most recent kernel you can to get the latest support for firewire. What kernel do you have?

post the output of 
```

uname -a

```

---

### Post by Rizado on 2008-02-05
> **stmiller said:**
> Firewire has been under heavy development in the Linux kernel over the past couple of major kernel releases. Depending on what firewire controller is on the external drive box, you may have good or bad luck. 

Update to the most recent kernel you can to get the latest support for firewire. What kernel do you have?

post the output of 
```

uname -a

```Well right now I don't have anything except the feisty live cd as my harddrive crashed. Anyway on the live cd I have: ```
Linux ubuntu 2.6.20-15-powerpc #3 Sun Apr 15 06:45:49 UTC 2007 ppc GNU/Linux
```I'm almost sure that some kernel upgrade to feisty this summer broke my firewire support. And the kernel I got when I upgraded to gutsy was completely broken. I had to compile my own and that was kernel 2.6.23.8. I tried both the new firewire stack and the old with no result.

I'm not sure it's the kernel that broke support or some other update but nothing showed up in dmesg until I unplugged the drive. I got a message that said something about master root something something. Anyway I'll try to reinstall everything this weekend and then I should be able to find out more.

BTW is it possible to unmount the live cd and mount a iso image of it in a live system on the go? And is it possible to install gutsy from a feisty live cd? I wonder because I don't have any cds left...

---

### Post by stream303 on 2008-02-05
Ok, you guys motivated me to get my external firewire loaded and booting Gutsy.

If you like, I can walk you through it if you want your firewire to be bootable.  It isn't that hard really.  Check this out:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

Step 1 would be to boot from anything, and issue the command:

```
find -proc/device-tree -name `sbp-2@*`
```

Don't forget the back-ticks..

---

