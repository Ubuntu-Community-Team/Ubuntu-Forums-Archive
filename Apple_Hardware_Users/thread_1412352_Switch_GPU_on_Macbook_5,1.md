---
title: "Switch GPU on Macbook 5,1"
date: 2010-02-21
forum: Apple Hardware Users
---

### Post by SwedishWings on 2010-02-21
Is there any way to switch to the nVidia 9400 controller in Ubuntu 9.04 on Macbook 5,1? 

When i run lspci i can't see the 9400 controller:

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)

```

Thanks,
Mike

---

### Post by linuxopjemac on 2010-02-21
did you go to the latest nvidia driver? (190.53 I think)

---

### Post by SwedishWings on 2010-02-21
> **linuxopjemac said:**
> did you go to the latest nvidia driver? (190.53 I think)

Thanks for your reply!

I have NVIDIA Driver Version 180.44. This is the default in 9.04 i think (i have all updates as of today). Is it advisable to download directly from nVidias site (version 190.53 currently)?

Would another driver find the 9400 controller on the PCI bus, when not lspci does so? I have a feeling it's more to it than just the driver.

/Mike

---

### Post by linuxopjemac on 2010-02-21
I have no idea about other drivers. I would remove your nvidia from synaptics and then install from the website.

---

### Post by linuxopjemac on 2010-02-21
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by SwedishWings on 2010-02-21
> **linuxopjemac said:**
> [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Thanks!

I installed version 190.53, but i have the same issue. lspci still can't see the 9400 controller: 

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)

```

I can't upgrade to 9.10 at this point (which might solve the issue) as my target system i'm developing code for is 9.04 :(

Any ideas?

/Mike

---

### Post by buntuLo on 2010-02-21
nvidia180 is prefectly able to drive your 9400m. the choice of which graphic card is done via EFI booting on macosx, while only the 9600mgt is enabled on bios-emulation boot (windows and linux).
you can boot linux via grub2-efi, many people have succesfully enabled the other card then changing their xorg.conf file.
still, setting up grub-efi isn't that straightforward to do, at least for me, and i'm not sure it works with karmic 9.10 (it did with jaunty 9.04). just search in this forum for EFI external booting and you'll find a very long thread about it. good luck, and report back here if you succeed!

---

### Post by SwedishWings on 2010-02-21
> **buntuLo said:**
> nvidia180 is prefectly able to drive your 9400m. the choice of which graphic card is done via EFI booting on macosx, while only the 9600mgt is enabled on bios-emulation boot (windows and linux).
you can boot linux via grub2-efi, many people have succesfully enabled the other card then changing their xorg.conf file.
still, setting up grub-efi isn't that straightforward to do, at least for me, and i'm not sure it works with karmic 9.10 (it did with jaunty 9.04). just search in this forum for EFI external booting and you'll find a very long thread about it. good luck, and report back here if you succeed!

Many thanks, that made sense.

Is grub-efi the same as GRUB2? I've read a bit and got pretty confused.

If there is great chance of screwing up the OSX partition (or the Linux partition for that matter), i think i wont try. Have no time to repair a broken machine now...

Thanks,
Mike

---

### Post by buntuLo on 2010-02-21
> **SwedishWings said:**
> Is grub-efi the same as GRUB2? I've read a bit and got pretty confused.
there are two different versions of grub2: grub-pc and grub-efi. by default karmic installs grub-pc
> **SwedishWings said:**
> If there is great chance of screwing up the OSX partition (or the Linux partition for that matter), i think i wont try. Have no time to repair a broken machine now...
well, i'd say not too much, and least not to damage partitions. but obviously you'd be playing with the bootloader, so you DO risk to make your system not bootable any more. not risky, if you're comfortable recovering your system also from a terminal running a livecd.
obviously, a backup is strongly recommended, cause making mistakes happens :~)

---

### Post by emrys on 2010-06-17
Any news on activating Nvidia 9400 on dual 9400/9600 systems? Still nothing in Lucid.

I've found this thread in the Gentoo forums that maybe can be helpful:
[http://forums.gentoo.org/viewtopic-t-750017-postdays-0-postorder-asc-start-25.html?sid=f926230e8d04079404555106ed2ae08c](http://forums.gentoo.org/viewtopic-t-750017-postdays-0-postorder-asc-start-25.html?sid=f926230e8d04079404555106ed2ae08c)

There is also a bug report on the issue: 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/592086](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/592086)

Anyone experimented with grub-efi? I can't take the risk as this is my work computer...

---

### Post by emrys on 2010-06-23
Apparently our problems will be solved using 2.6.34 kernel

From: [http://kernelnewbies.org/LinuxChanges#head-5c0a6ff5325bae07a1d5ff12b0c33b89f2128173](http://kernelnewbies.org/LinuxChanges#head-5c0a6ff5325bae07a1d5ff12b0c33b89f2128173)

"1.10. GPU switching
Some laptops have two GPUs, a low-power and inefficient GPU and a high-power and powerful GPU. Users should be able to switch to one or another at runtime. In this version, Linux adds support for this feature. You need to restart X, though."

Any hope of a backport to Lucid?

---

### Post by SwedishWings on 2010-06-23
> **emrys said:**
> Apparently our problems will be solved using 2.6.34 kernel

From: [http://kernelnewbies.org/LinuxChanges#head-5c0a6ff5325bae07a1d5ff12b0c33b89f2128173](http://kernelnewbies.org/LinuxChanges#head-5c0a6ff5325bae07a1d5ff12b0c33b89f2128173)

"1.10. GPU switching
Some laptops have two GPUs, a low-power and inefficient GPU and a high-power and powerful GPU. Users should be able to switch to one or another at runtime. In this version, Linux adds support for this feature. You need to restart X, though."

Any hope of a backport to Lucid?

Thanks for the information, good news indeed!

I really hope there will be a backport to Lucid.

EDIT: I think the information in [COLOR="Red"][this link]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=6a9ee8af344e3bd7dbd61e67037096cdf7f83289")[/COLOR] is bad news, seem to not work on MacBook at all.

Thanks,
Mike

---

### Post by alexmurray on 2010-06-24
Indeed - the problem is that booting in legacy bios mode disables the 9400M completely - to enable it you have to boot via EFI and then you can simply choose which one you want by specifying the corresponding PCI ID in your xorg.conf

---

### Post by Helios747 on 2010-06-25
> I installed version 190.53, but i have the same issue. lspci still can't see the 9400 controller: 


uh

> 02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)


??

also just to add my input, I have the same MacBook (only my GPU is a 9400M, no GT), and installing the latest nvidia drivers from the website worked fine. If you are using Lucid however you will need to follow [http://ubuntuforums.org/showpost.php?p=9211609&postcount=35]("http://ubuntuforums.org/showpost.php?p=9211609&postcount=35") <-- that post to get it to install correctly.

Also,

> Indeed - the problem is that booting in legacy bios mode disables the 9400M completely - to enable it you have to boot via EFI and then you can simply choose which one you want by specifying the corresponding PCI ID in your xorg.conf

I have a MP 5,1 single legacy booting 10.04 and it sees the GPU fine. AFAIK it's the EFI booting that doesn't support 3D acceleration.

---

### Post by Gelliray on 2010-06-25
> **SwedishWings said:**
> Is there any way to switch to the nVidia 9400 controller in Ubuntu 9.04 on Macbook 5,1? 

When i run lspci i can't see the 9400 controller:

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)

```

Thanks,
Mike
i got it , thank you very much!

---

### Post by Gelliray on 2010-06-25
It is really a complicated process. but finally. I got it , thank you very much!

---

### Post by SwedishWings on 2010-06-25
> **Helios747 said:**
> I have a MP 5,1 single legacy booting 10.04 and it sees the GPU fine. AFAIK it's the EFI booting that doesn't support 3D acceleration.

Just so i understand: With the latest nVidia drivers, you can see **_both_** the 9400 and the 9600 video chip via lspci?

---

### Post by alexmurray on 2010-06-25
> **SwedishWings said:**
> Just so i understand: With the latest nVidia drivers, you can see **_both_** the 9400 and the 9600 video chip via lspci?
No - Helios747 only has a MacBook 5,1  (i.e. not a Pro) which only has the 9400M, so of course it can be seen with legacy bios boot.

The MacBook Pro 5,1 has 2 GPUs (9400M + 9600M GT), but only the 9600M GT can be seen with bios boot - the 9400M is only unlocked when EFI booting - so the only way to try and use the 9400M is EFI booting.

---

### Post by SwedishWings on 2010-06-25
Ok, so the only way to use the 9400 chip is to use grub-EFI. I have looked around but get confused with lengthy threads with conflicting instructions...  

Is there a one-stop proven how-to for making this work? Or could someone with experience write one? I would much appreciate it, and i guess others would as well.

Thanks in advance,
Mike

---

### Post by Helios747 on 2010-06-25
-facepalm-

Doh! I wasn't aware you were talking about the macbook PRO, my apologies.

---

### Post by emrys on 2010-07-04
> **SwedishWings said:**
> Ok, so the only way to use the 9400 chip is to use grub-EFI. I have looked around but get confused with lengthy threads with conflicting instructions...  

Is there a one-stop proven how-to for making this work? Or could someone with experience write one? I would much appreciate it, and i guess others would as well.

Thanks in advance,
Mike

Yes, please, someone out there tried it and got it?

It would be great to have a clear and simple howto.

Gelliray, did you manage to get 9400 working?

Thanks

---

### Post by dromiceiomimus on 2010-07-06
+ 1 for an overview..

I spent some time messing with grub this weekend but it does appear to be a bit convoluted. FWIW I put the 9600M GT in low power mode and my 5,1 is running a bit cooler.  Any help, even if it's not step by step would be much appreciated..

---

### Post by emrys on 2010-07-06
> **dromiceiomimus said:**
> + 1 for an overview..

I spent some time messing with grub this weekend but it does appear to be a bit convoluted. FWIW I put the 9600M GT in low power mode and my 5,1 is running a bit cooler.  Any help, even if it's not step by step would be much appreciated..

dromiceiomimus, how did you put it in low power mode?

Thanks.

---

### Post by dromiceiomimus on 2010-07-06
> **emrys said:**
> dromiceiomimus, how did you put it in low power mode?

Thanks.

Just edit your xorg.conf: 
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid#Set%20Graphics%20Card%20to%20Powersave%20Mode](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid#Set%20Graphics%20Card%20to%20Powersave%20Mode)


Also, I have my fan1_min set to 4500:
`echo 4500 | sudo tee /sys/devices/platform/applesmc.768/fan1_min`

---

### Post by SwedishWings on 2010-07-07
Regarding fan control: i wrote a daemon in C a while ago to keep the fan dynamically at a higher speed, and lowering the temp. It uses the temp sensors to determine the overall temp and adjust fan speed accordingly. It has a config file that can be used to trim the temp. My MBP is running a lot cooler this way....

I'm happy to share it if anyone want it.

/mike

---

### Post by buntuLo on 2010-07-07
> **dromiceiomimus said:**
> Just edit your xorg.conf: 
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid#Set%20Graphics%20Card%20to%20Powersave%20Mode](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid#Set%20Graphics%20Card%20to%20Powersave%20Mode)

hi, i'm on mbp5.1 and i don't manage to get this working. i modified xorg.conf, rebooted, anf the nvidia-settings interface shows me that i'm still runnning in max performance mode. if i disconnect the main power, it is detected in real time in the gui, but the mode still does not change.
i attach a snapshot of the nvidia-settings gui, showing also my Device section of xorg.conf.
fyi, i'm runnig karmic-amd64 with nvidia-195. i also noted that other people running the same driver have an extra drop-down menu in nvidia-settings, which allow to change the performance mode. do you guys have that, or does your powermizer tab look like mine?
thanks and ciao, Lo.

ps: SwedishWings, i'd love to check out your script and give it a try. there should be other threads about the fan issue: it is maybe more appropriate to put it there, or open a new one. thanks a lot!

---

