---
title: "Ubuntu 24.04 Freezing on MacBook Pro (Mid-2010) unless nomodeset passed at boot"
date: 2024-06-11
forum: Apple Hardware Users
---

### Post by fbagnato1 on 2024-06-11
Hello all,

I have installed Ubuntu 24.04 on a MacBook Pro (Mid-2010) laptop.

The laptop was experiencing regular freezing, only recoverable by turning off the power and restarting the laptop.

After asking for help on the #ubuntu IRC configuring grub with the line GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" seems to have fixed the freezing, now no longer occurring.

When I check the video drivers, it is now using a "VGA compatible controller" driver for both video adapters which are 1) NVIDIA GeForce GT 330M and 2) Core Processor Integrated Graphics Controller whereas it was previously using the nouveau and intel drivers for the video adapters.

I have been told that there are no native drivers for the NVIDIA GeForce GT 330M in Ubuntu 24.04, not sure about the Core Processor Integrated Graphics Controller.

Have I lost functionality by using "VGA compatible controller" driver for both video adapters?

If so other than running Ubuntu with nomodeset is there something I can do to get nouveau working without freezing?

For example I tried temporarily replacing nomodeset with nouveau.noaccel=1 then with nouveau.nofbaccel=1 but both caused the booting to freeze.

I would like to try and eliminate nomodeset as it has also defaulted the Core Processor Integrated Graphics Controller to the "VGA compatible controller" driver.

I prefer to get nouveau working albeit with some compromises.


Regards,

fbagnato

---

### Post by yancek on 2024-06-11
The graphics chip you have was released in 2010 so it may not work with Ubuntu 24.04 so have you tried the methods suggested at the link below to install the driver?  The link references Ubuntu 20.04 specifically so I don't know if any of the methods will work but it should be worth a try if you haven't done this already.

[https://www.redswitches.com/blog/install-nvidia-drivers-on-ubuntu-20-04/](https://www.redswitches.com/blog/install-nvidia-drivers-on-ubuntu-20-04/)

---

### Post by fbagnato1 on 2024-06-12
Hello yancek,

Thanks for your reply.

I tried all three methods in the link you provided but without success.

However, in method 3 - Install NVIDIA Beta Drivers via the PPA Repository I found the following:

When I added the repository using the command in step 1) > Add the PPA GPU Drivers Repository to the System by running the command

```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

I see in the outputted text that it mentions:

> ## Legacy releases

96.43.23 (x86 / x86_64) - GeForce 2 through GeForce 4 series GPUs (*)

Which should cover my NVIDIA GeForce GT 330M adapter however if I then run step 2) > Find Your GPU Model and See the Available Drivers the only device outputted is my Wifi adapter which already has proprietary drivers installed.

Does that mean that the relative text outputted is not updated to reflect Ubuntu 24.04 and that there are actually no Beta drivers in the PPA for the NVIDIA GeForce GT 330M?

I tried temporarily removing nomodeset and retrying the step 2) > Find Your GPU Model and See the Available Drivers but got the same response from the command.

I also tried replacing nomodeset with nouveau.modeset=0 to disable nouveau  but got a blank screen whilst booting (I've seen this blank screen  reported by others on the web).

I also looked into the NvClkMode parameter and it is not supported on the NVIDIA GeForce GT 330M.

I am wondering if there are any other parameters I can pass to the nouveau driver to see if I can resolve the problem.

Regards,

fbagnato

---

### Post by howefield on 2024-06-12
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by fbagnato1 on 2024-06-14
Since setting the grub setting to GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" to fix the problem I experimented with the nouveau  parameters and found another workaround which is a better solution as it  still leaves the original video drivers loaded (where as the setting  nomodeset replaces the original video drivers with the standard VGA  driver). 
Setting the grub setting to GRUB_CMDLINE_LINUX_DEFAULT="nouveau.NvMXMDCB=0" fixes the freezing.

---

### Post by ajgreeny on 2024-06-14
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction.
It is a great help to other users searching the forum.

---

