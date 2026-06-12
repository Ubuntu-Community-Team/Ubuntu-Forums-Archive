---
title: "No sound in 7.10"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Binary Dragon on 2007-11-06
I recently install Ubuntu 7.10 on my HP Pavilion dv9540us laptop, and I have not been able to get the sound to work.  By no sound, I mean no sound at all.  No system, video, mp3, application, etc sounds from either the built in speakers nor from headphones if I connect those.  I've tried a number of things I've found in various forums and walkthroughs to no avail.  Hopefully someone here can help me figure this out.

As I'm sure it'll be asked for, here's my lspci output.
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
mike@Galileo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by Arthur Archnix on 2007-11-06
What does this return?
```
aplay -l
```
And are you dual booting with windows? Have you ran 
```
alsaconf
```
and unmuted everthing?

---

### Post by Binary Dragon on 2007-11-07
aplay -l returns

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I am dual booting with Windows Vista.  Each OS has its own HDD.  Sound works perfectly on Vista, so I'm confident it's not a hardware issue, but something at the software level.

Yes, I did run alsaconf and made sure everything was unmuted.

---

### Post by Harpoon on 2007-11-07
I, too, am hoping for an answer to this one.  I have a Lenovo N100 laptop with Feisty  x64 running - - same intel sound card as listed above.  When I tried the Gutsy live cd it seemed I had some sound (bad, to be sure) coming from the laptop speakers, but none from the connected amplified speakers.  I am waiting to get a clue as to how to fix it before making the switch.

---

### Post by Inxsible on 2007-11-07
Binary Dragon, I have a similar laptop as yours (dv9000t). My sound worked out of the box. I don't remember my sound card now (@work on XP :( ). I probably have the same as yours.

You have probably tried this already, but oh well
```
alsamixer
``` Make sure all the levels are set to max

---

### Post by Arthur Archnix on 2007-11-07
I have an hp 530, intel sound card. Vista sound worked perfect, nothing in Ubuntu (or any other distro). There is a guide to troubleshooting sound that you should follow. I did, though it had no effect.

I can't tell you what the problem is, bios maybe, vista (xp has same issue), but if you're affected by the same bug as me I've only found 3 fixes.

1. Sometimes, rebooting and resetting the bios to default, save, exit, reboot, sometimes that works. You might want to switch it up a bit too. Reboot, reset, power down, power on. And try two or three times. This once got my sound working while dual booting.

2. You might try using the hp erase utility found in the bios. Completely erase hard-drive. Reinstall  vista. Delete all partitions but vista (i.e., backup partitions), move vista partition, shrink, set ubuntu partition as second, install. This worked for me once. Though I had to mix in the trick number one above as well.

3. Sure fire fix. Works every time. Erase hard-drive. Install ubuntu. When not dual booting, sound works fine.

Try other guides first, I did this as a last ditch effort, obviously, since it involves a lot of work.

---

### Post by Binary Dragon on 2007-11-20
I'm now on pure Linux (no Vista dual boot) and I still can't get any sound.  I've tried numerous reinstallations of Ubuntu (mostly because I keep breaking Ubuntu trying to make the sound work) and no luck.  Any suggestions?

---

### Post by Dr Small on 2007-11-20
> **Binary Dragon said:**
> I'm now on pure Linux (no XP dual boot) and I still can't get any sound.  I've tried numerous reinstallations of Ubuntu (mostly because I keep breaking Ubuntu trying to make the sound work) and no luck.  Any suggestions?
If you have onboard sound, have you checked to make sure it is enabled in the BIOS ?

---

### Post by Arthur Archnix on 2007-11-20
Well, as I said, I've never found anyone for whom my fix has worked. More people have success following the complete sound solutions guide here on the forums. On my HP laptop, the fix that works for me is:

Reboot. F10 to enter bios. Choose reset defaults, F10 to save. Choose exit, F10 to save and exit. As it reboots but before 'press F10' comes up on screen, do a hard power down, hold power key until power down. Then restart. Should have sound.

Again, this has worked for me, but no one else. You'd be much better off by following the complete sound solutions guide on the forum.

---

### Post by Binary Dragon on 2007-11-20
The BIOS doesn't have any options related to sound except for "Button Sound" which is enabled.  Again, when I had Vista, the sound worked perfectly in it, and other than install Ubuntu a number of times, I have done nothing to the computer that would make it not work.

If it helps any, my computer is a laptop (HP Pavillion dv9540) with two HDDs.  Ubuntu is currently installed on the first HDD with the second mounting as /home.

---

### Post by Arthur Archnix on 2007-11-20
Mine doesn't either. Like I said, my steps shouldn't work and probably don't. Except that, for me, they do. But what will probably work for you is the complete sound solution guide.

---

### Post by Binary Dragon on 2007-11-20
I've tried the solution guide to the best of my ability.  Nothing seems to have helped.  I've managed to collect the information that might be helpful at
[http://pastebin.ca/792012](http://pastebin.ca/792012)

If anyone has any suggestions, please let me know.  I love Ubuntu, but I can't stick with it if I can't get the sound to work.

---

