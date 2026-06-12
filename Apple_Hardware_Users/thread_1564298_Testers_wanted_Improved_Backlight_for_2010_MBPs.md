---
title: "Testers wanted: Improved Backlight for 2010 MBPs"
date: 2010-08-30
forum: Apple Hardware Users
---

### Post by Sidolin on 2010-08-30
Hello everyone,

while investigating gpu switching on a mbp 6,2 I discovered how apple does the backlight setting on the recent mbps.

I added the new method to mbp_nvidia_bl, but as I have only access to one mbp it would be great if someone could test it on other models. Benefits include smooth transitions between brightness levels (like on osx) and doing stuff the right way.

Please only test this if you have sufficient knowledge of installing kernel modules and general linux stuff. And as everything hardware related it's possibly dangerous, just in case.

Howto: Remove all old backlight modules, download source, install it, modprobe mbp_nvidia_bl debug=1, cd /sys/devices/virtual/backlight/mbp_backlight, cat actual_brightness, echo 1 > brightness, echo 15 > brightness.
Additional points for posting the relevant dmesg output from the module here, especially the mux version.

This might also work for older mbps with graphics switching, for this edit /usr/src/mbp_nvidia_bl-0.24.3/mbp_nvidia_bl.c, find your model in the table and replace "nvidia_chipset_data" with "gmux_chipset_data". 

Thanks! :D

---

### Post by itismike on 2010-08-30
Hi Sidolin,

I shouldn't be doing this given my lack of kernel experience, but I'm incorrigible. I got stuck at package installation:
```
$ sudo dpkg -i mbp-nvidia-bl-dkms_0.24.3_all.deb 
Selecting previously deselected package mbp-nvidia-bl-dkms.
(Reading database ... 151409 files and directories currently installed.)
Unpacking mbp-nvidia-bl-dkms (from mbp-nvidia-bl-dkms_0.24.3_all.deb) ...
Setting up mbp-nvidia-bl-dkms (0.24.3) ...
No packages found matching mbp_nvidia_bl-dkms.
Need NAME, and VERSION defined
ARCH is optional
dpkg: error processing mbp-nvidia-bl-dkms (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mbp-nvidia-bl-dkms
```

---

### Post by Sidolin on 2010-08-30
It seems packaging a kernel module is a lot harder than writing one so i'm giving up trying to build a neat .deb. I attached the source to the first post, maybe someone is better at packaging than me. May be it works with loadtarball, probably works if you just install the old mbp_nvidia_bl and replace the .c in /usr/src/mbp_nvidia_bl with mine from the tar.bz2 and rebuild the kernel module with dkms.

---

### Post by _mario_ on 2010-09-15
Hi,

I'm currently preparing an update of this package for maverick and I'd like to include your patches of course. Can your provide some more information?

1. Where did you get the mechanism from?
2. What is the formula while writing (outl(0x1af40 / 15 * intensity, 0x774)) and reading (intensity = inl(0x774) / 0x1cc0) used for? If it is to scale to 15 levels as the old interface provided, we can omit it. Scaling to a reasonable range should better be left to userland applications (i.e., g-p-m). The older inferfaces were just that limited. What's the true hardware range?
3. .iostart and .iolen should reflect the true hardware resources being operated. Which ports exactly does the driver need? 0x704-0x707 to get the hardware version? And exactly 0x774 to read write the brightness?

thanks & ciao,
Mario

---

### Post by Sidolin on 2010-09-16
> 1. Where did you get the mechanism from?

Putting ```
agclog=10000 agcdebug=4294967295
``` in /Library/Preferences/SystemConfiguration/com.apple.Boot.plist enables logging for graphics switching and backlight control. It's quite verbose, output can be found in /var/log/kernel.log.

> 2. What is the formula while writing (outl(0x1af40 / 15 * intensity, 0x774)) and reading (intensity = inl(0x774) / 0x1cc0) used for? If it is to scale to 15 levels as the old interface provided, we can omit it. Scaling to a reasonable range should better be left to userland applications (i.e., g-p-m). The older inferfaces were just that limited. What's the true hardware range?

It's just for scaling, it's possible to use other values as well. I guess the hardware range is 0 - 0x1af40 since that seems to be what osx sets when at full brightness. Setting higher values is possible but i didn't notice any difference when going even higher.

> 3. .iostart and .iolen should reflect the true hardware resources being operated. Which ports exactly does the driver need? 0x704-0x707 to get the hardware version?


The real range is found in the acpi dsdt, search for gmux. It starts at 0x700 and is 0xff long. 
A problem is that the other ports in this region do things like switching the display or powering down the nvidia gpu so I started to write a general gmux driver which does all these things, among setting the brightness. But it's still under heavy development so it certainly won't be ready for maverick. You can find the current version at [http://andreas.meetr.de/gmux/apple_gmux.c](http://andreas.meetr.de/gmux/apple_gmux.c) but it's not really ready yet.

> And exactly 0x774 to read write the brightness?
0x774 works for my laptop (mbp 6,2) but if you look at the kernel log it also sets 0x724, I'm not sure why.

---

### Post by metatechbe on 2010-09-16
Sidolin,

You are doing great progress !

I have a few questions : 
- I tried to activate the "agcdebug" on my MBP 2009 but my kernel.log does not show anything. Is there an equivalent for these models ? 
- should the apple_gmux.c work on MBP 2009 with 2 graphic cards ?
- do the brightness & graphic card controls work in EFI mode ?
- in BIOS mode does "lspci" report both graphic cards ?
- how do you find the address of the acpi dsdt ? 

Thanks,

metatechbe

---

### Post by Sidolin on 2010-09-16
> **metatechbe said:**
> 
- I tried to activate the "agcdebug" on my MBP 2009 but my kernel.log does not show anything. Is there an equivalent for these models ?


Did you reboot afterwards? Can you paste your full Boot.plist?

> **metatechbe said:**
> 
- should the apple_gmux.c work on MBP 2009 with 2 graphic cards ?


Not at the moment, but after a few modifications it could work. At least if apple didn't change how the gmux works. But at least the detection which graphics card is the integrated one and the check for the gmux hardware revision have to be changed beforehand.

> **metatechbe said:**
> 
- do the brightness & graphic card controls work in EFI mode ?


Yes. If brightness control or apple_smc doesn't work for you in EFI mode it's probably because you use the noefi boot parameter which disables dmi (to check just run dmidecode, if it doesn't output your model etc. dmi doesn't work) which is used by some drivers to detect the model. 
This patch (not by me) let's you boot without noefi: [http://140.211.166.79/mailarchive/linux-kernel/2010/8/16/4607435/thread](http://140.211.166.79/mailarchive/linux-kernel/2010/8/16/4607435/thread)

> **metatechbe said:**
> 
- in BIOS mode does "lspci" report both graphic cards ?


No, BIOS mode hides the integrated card. Maybe it's possible to somehow unhide it but for now the intel card requires efi.

> **metatechbe said:**
> 
- how do you find the address of the acpi dsdt ? 


```
sudo apt-get install acpidump iasl
sudo acpidump > acpidump.txt && sudo acpixtract acpidump.txt && iasl -d DSDT.dat && ls -l DSDT.dsl

```

---

### Post by metatechbe on 2010-09-17
Hi Sidolin,

Thanks for your responses...

> **Sidolin said:**
> Did you reboot afterwards? Can you paste your full Boot.plist?


Regarding the AGC log not working, I was still running under MacOS 10.6.1, so after upgrading to 10.6.4 I get the following entries in the log (amongs many others):

```
Sep 17 22:16:39 MBP kernel[0]: AGC: 2.8.63, HW version=1.8.8, flags:0, features:4
Sep 17 22:16:57 MBP kernel[0]: AGC:: setMuxRegister:1444 (750, 1, 1)
Sep 17 22:16:57 MBP kernel[0]: AGC:: setMuxRegister:1444 (750, 1, 0)
Sep 17 22:16:57 MBP kernel[0]: AGC:: getMuxRegister:1425 (716, 1) = 5
Sep 17 22:16:57 MBP kernel[0]: AGC:: setMuxRegister:1444 (714, 1, 0)

```> **metatechbe said:**
> 
- should the apple_gmux.c work on MBP 2009 with 2 graphic cards ?


> **Sidolin said:**
> 
Not at the moment, but after a few modifications it could work. At least if apple didn't change how the gmux works. But at least the detection which graphics card is the integrated one and the check for the gmux hardware revision have to be changed beforehand.


Apart from the 0x8086 PCI Device ID, do you foresee anything else that will need modifications ? If you need more debug info, please ask.

> **Sidolin said:**
> 
```
sudo apt-get install acpidump iasl
sudo acpidump > acpidump.txt && sudo acpixtract acpidump.txt && iasl -d DSDT.dat && ls -l DSDT.dsl

```

```

Device (GMUX)
{
    Name (_HID, EisaId ("APP000B"))
    Name (_CID, "gmux")
    Name (_STA, 0x0B)
    Name (_CRS, ResourceTemplate ()
    {
        IO (Decode16,
            0x0700,             // Range Minimum
            0x07FF,             // Range Maximum
            0x01,               // Alignment
            0xFF,               // Length
            )
    })

```The gmux range on the MBP 2009 (MacBookPro5,3) also starts at 0x700 and is 0xff long.

If you have a version that should work on MBP 2009, I can try it.

Regards,

Metatechbe

---

### Post by Sidolin on 2010-09-18
Well that looks promising, almost no difference to the newer mbps. And I guess the only things that need to get changed really are just the device id and the gmux version check to include 1.8.

But the switching driver is just one part, the other being the graphics card driver which also has to support switching. It's only possible with nouveau at the moment and I don't know if the current implementation supports two nvidia cards instead of just one nvidia and one intel. But thats certainly fixable.

I'll be on vacation for two weeks starting tomorrow without any internet access or time for developing anything, but I'll certainly try to finish the driver afterwards. There are still a few other things that need fixing (such as suspend not working, some audio hardware on the dedicated card interfering, proper hardware detection etc.) so it could take a while. 
But I'm happy to have someone who could test it on some other hardware, and as far as I know there are no other dual gpu configurations from apple?

---

### Post by metatechbe on 2010-09-25
Sidolin,

Thanks to your findings, this other thread's long standing quest was finally solved.
[http://ubuntuforums.org/showthread.php?t=1076879](http://ubuntuforums.org/showthread.php?t=1076879)

For your information, a MacBookPro5,1 has a gMux version of 1.7.3, so it would be nice if your switching driver would also recognize this model.

Thanks again,

metatech

---

### Post by tmg1981 on 2010-09-27
Hi Sidolin,

many thanks for your effort and sharing your knowledge. As metatech said, you made a lot of people happy. ;)
I have a MBP5,1 with gmux 1.7.3. Disabling the 9600M GT works by writing "0" to port 0x750, however, changing the brightness does not.
Writing different values to port 0x774 doesn't have any effect yet. Heres a dump of my kernel log in MAC OS X:
```

Sep 27 10:30:01 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x2)
Sep 27 10:30:01 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x2)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0x9, 0x3, 0xffffff800c7626a8)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0xa, 0x3, 0xffffff800c7626a8)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0x9, 0x3, 0xffffff800c7626d0)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0xa, 0x3, 0xffffff800c7626d0)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x3)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x3)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x3)
Sep 27 10:30:02 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x3)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: getMuxRegister:1425 (716, 1) = 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 58, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 51, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 45, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 38, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 32, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 26, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 19, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 13, output = 47
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 6, output = 47




Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:04 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 0, output = 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0, 0, 0, 0)
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:04 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0x9, 0x2, 0xffffff800c7626a8)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0xa, 0x2, 0xffffff800c7626a8)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0x9, 0x2, 0xffffff800c7626d0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0xa, 0x2, 0xffffff800c7626d0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x2)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x2)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x2)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x2)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0x9, 0x3, 0xffffff800c7626a8)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0xa, 0x3, 0xffffff800c7626a8)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0x9, 0x3, 0xffffff800c7626d0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0xa, 0x3, 0xffffff800c7626d0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x3)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x3)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x3)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x3)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 6, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 13, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 19, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 26, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 32, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 38, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)




Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 45, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 51, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 58, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:06 laptop-2 kernel[0]: AGCBL:: doIntegerSet:520 (1), input value = 64, output = 47
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (10724, 2, 2f)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0010, 0x2f, 0, 0, 0)
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: UpdateSyncPWM:1239 0
Sep 27 10:30:06 laptop-2 kernel[0]: AGC:: setMuxRegister:1444 (774, 4, dff)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0x9, 0x2, 0xffffff800c7626a8)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0xa, 0x2, 0xffffff800c7626a8)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0x9, 0x2, 0xffffff800c7626d0)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0xa, 0x2, 0xffffff800c7626d0)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x2)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x2)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x2)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x2)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0x9, 0x3, 0xffffff800c7626a8)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5ce800, 0xa, 0x3, 0xffffff800c7626a8)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0x9, 0x3, 0xffffff800c7626d0)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: messageAsync:95 (0xac0004, 0xffffff800c5cc800, 0xa, 0x3, 0xffffff800c7626d0)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x3)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->Internal.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x3)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyWillChangeSpeed, 0x3)
Sep 27 10:30:08 laptop-2 kernel[0]: AGC:: _doActionFBNotification:196 (IGD->External.fb [0xffffff800c762640], kIOFBNotifyDidChangeSpeed, 0x3)
```

It shows the kernel log when I switch from brightness level 1 to 0 and back to 1.
I'm not very familiar with the OS X internals, so maybe you can tell me more about it.
I also tried writing to port 0x10724, as it is done according to the log. Doesn't change anything either.

Again many thanks and keep on rocking,

Thomas

---

### Post by Sidolin on 2010-09-27
Hey, against my expectations we have (kind of flaky) wifi here at the hotel so i can check these forums from time to time.
It's great to see some partial success on other mbps and even some people also trying to figure out what's needed to support them.

As for the backlight, try writing to port 0x724 instead if 10724 as the port range of the gmux chip is just 0x700 +0xFF so it doesn't make any sense to write to a port starting with 10xxx. I've also seen some write to 20xxx but I'm not sure why.

Also note that 0x2f = 47 decimal:
doIntegerSet:520 (1), input value = 38, output = 47
setMuxRegister:1444 (10724, 2, 2f)

---

### Post by tmg1981 on 2010-09-28
Hi again,

unfortunately, writing at 0x724 does not work either. Hmm, I'm a bit confused...
Sidolin, what is you system configuration? (Ubuntu version, kernel version, nvidia-dirvers or nouveau, ...)?

Thanks again...!

---

### Post by Sidolin on 2010-09-28
I'm using a mbp 6,2, 2.6.36-rc3 with some patches and ubuntu maverick. It's possible that something else is needed for controlling the backlight, there are quite a few ports that seem to be connected somehow to this. Another blind guess is port 0x770, otherwise I can't really help you.

---

### Post by tmg1981 on 2010-09-29
Hi Sidolin,

thanks...but 0x700 as well doesn't give any effect.
What graphics driver do you use? And which version?


Greetings,

Thomas

---

### Post by Sidolin on 2010-09-30
It's 0x770 not 0x700, 0x700 seems to be pretty static for me, I haven't observed a single change of it's value yet. 

What also could be useful is the log for a suspend/resume-cycle as the driver saves and logs some or maybe all important values when suspending so it's a useful thing to get the whole state when debugging.

Oh and I'm using nouveau as there is no switching support for the proprietary driver, using the nouveau git kernel and maverick libraries.

---

### Post by _mario_ on 2010-10-12
> **ayushiinfotech said:**
> i did not understand can explain briefly.................?
advance thanks .........:KS

Sidolin's changes have been merged into the mactel PPA's version of mbp_nvidia_bl in the meantime. If you have a MacBook Pro 6,1 or 6,2, please confirm whether it is indeed working and report back.

ciao,
Mario

---

### Post by tmg1981 on 2010-10-17
Hi,

so for MBP 5,1 it isn't working. I know, you said 6,1 and up. ;)
Just FYI

Greetz
Thomas

---

### Post by lael on 2010-10-18
> **_mario_ said:**
> Sidolin's changes have been merged into the mactel PPA's version of mbp_nvidia_bl in the meantime. If you have a MacBook Pro 6,1 or 6,2, please confirm whether it is indeed working and report back.

ciao,
Mario

Mario, 

My 2010 MBP 6,1 backlight was working fine back in the June timeframe, but I noticed that after an update (fairly recently), that the backlight support stopped working.  The key to bring the backlight brightness up does nothing, and the notification shows 1/16 (or whatever it is), but the brightness-down key turns the backlight off entirely.

I've got 0.25~lucid installed.  It looks like you updated this on 10/10.
[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

How can I help fix this?

[FONT="Courier New"]$ uname -r
2.6.32-24-generic[/FONT]

---

### Post by metatechbe on 2010-11-12
Easier method to obtain the gmux version (for future reference if needed) :

ioreg -l -p IOPower |grep gMux
                "gMux-version" = "1.8.8"

---

### Post by whittylp on 2011-03-25
> **itismike said:**
> Hi Sidolin,

I shouldn't be doing this given my lack of kernel experience, but I'm incorrigible. I got stuck at package installation:
```
$ sudo dpkg -i mbp-nvidia-bl-dkms_0.24.3_all.deb 
Selecting previously deselected package mbp-nvidia-bl-dkms.
(Reading database ... 151409 files and directories currently installed.)
Unpacking mbp-nvidia-bl-dkms (from mbp-nvidia-bl-dkms_0.24.3_all.deb) ...
Setting up mbp-nvidia-bl-dkms (0.24.3) ...
No packages found matching mbp_nvidia_bl-dkms.
Need NAME, and VERSION defined
ARCH is optional
dpkg: error processing mbp-nvidia-bl-dkms (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mbp-nvidia-bl-dkms
```

Hi, slightly off-topic, but this post is the top google response for "dkms Need NAME, and VERSION defined", so I'm putting my findings for it here:

I managed to work out the problem is in the "debianisation" of the package-name.  If you use underscores in your DKMS PACKAGE_NAME (eg source is in "mpb_nvidia_bl-0.24.3") you'll end up with a debianised package name mbp-nvidia-bl-dkms_0.24.3_all.deb, but internally the postinst script will be looking for a package named "mpb_nvidia_bl" to determine the VERSION.  Since this doesn't exist the VERSION is empty and we hit this error.  Change your PACKAGE_NAME (and source code directory) to eliminate the underscores and this should work.

Cheers,

Greg

---

### Post by tomodachi on 2011-06-12
I've kind of been lurking on this thread for quite some time now.
Thought I'd try to give something back.

I'm booting my MBP 5.x 
in efi mode 
My macbook has the dual nvidia setup
9400GT
9600GT



Sidolin mentions that switching isn't support with the proprietary driver.
I get it working using the proprietary driver. 


If you would like to try what I'm doing

do it in the following steps:
* boot in efi mode 
* make sure its single mode so X isn't started.
* unload the nvidia driver
* run gpupower to disable the 9600GT
* load the nvidia driver 
* start X

I'm using Ubuntu 11.04 with a stock kernel.
No brightness support though. But haven't really understood where to put the custom c file to recompile support (dont have anything with the same name in my fs, eventhough i have the nvidia-bl dkms package installed)
 


~ tomodachi

---

