---
title: "Professor fate --- the laptop and a few problems"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by professor fate on 2007-10-24
Hello,

First, I'm not sure where I should be posting these comments or questions.  I see there's a Dell support thread, then there's an Installation thread, a Beginner thread, and Cafe thread.  My first post was in the Beginner thread, but it was moved to Cafe.  For those that want to follow my 30 day journey, where should I post?

The laptop...

My buddy brought by an awesome laptop.  It's a Dell Vostro C2D, with 2GB memory, 120GB hard drive, Wifi (he told me it's a Dell 1390), Nvidia 8400M GS, and it's a smaller 14" screen.  He must have some serious pull at work, because that's where he got it from.  

OK...I installed the Gutsy CD and the live version booted up.  For starters I have no sound, no Wifi, and the video refresh rate is at 0.  Odd, I've never seen anything like that before.  I do have ethernet access though.

So...do I let this thing install by itself, or am I going to have to partition the drive?

PF

---

### Post by FuturePilot on 2007-10-24
One of the steps in the Installer will ask you how you want to partition the hard drive. Make sure you choose the step that says Resize and use Free Space. It should be the default option. You can adjust the size with the size with the slider.
As for the sound and wireless we need to know what the hardware is. So if you could open a terminal (Applications>Accessories>Terminal) and type
```
lspci
```
and just post the output of that.
The Gnome Screen Resolution tool likes to lie with Nvidia cards. Don't use that to adjust the refresh rate. You can do this with the Nvidia Settings tool that comes with the restricted driver. You can install that after you install Ubuntu. You will get a little notification about the driver after you reboot after the install is done.

This thread would probably do better in the Absolute Beginners forum.

---

### Post by professor fate on 2007-10-24
> **FuturePilot said:**
> One of the steps in the Installer will ask you how you want to partition the hard drive. Make sure you choose the step that says Resize and use Free Space. It should be the default option. You can adjust the size with the size with the slider.
As for the sound and wireless we need to know what the hardware is. So if you could open a terminal (Applications>Accessories>Terminal) and type
```
lspci
```
and just post the output of that.
The Gnome Screen Resolution tool likes to lie with Nvidia cards. Don't use that to adjust the refresh rate. You can do this with the Nvidia Settings tool that comes with the restricted driver. You can install that after you install Ubuntu. You will get a little notification about the driver after you reboot after the install is done.

This thread would probably do better in the Absolute Beginners forum.


I'm sending the info you requested as an attachment.  For some reason my ethernet on the Vostro when tits up, so I had to transfer the file to my work computer that can't read .odt documents.

---

### Post by professor fate on 2007-10-24
Hello,

Here is the info you initially wanted.  Ubuntu is installed, and I'm connected to the net via ethernet.  

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by FuturePilot on 2007-10-24
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```
That's your sound card. I also had no sound with that card. But you can easily get sound. Try [these]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")
instructions.

---

### Post by professor fate on 2007-10-24
OK, I will do that.

An update......
I noodled around this OS and found the package manager.  Through that I installed something called the Nvidia-glx-new and enabled the hi end graphics package (something you called compiz).  How do I make adjustments to that?

---

### Post by aaaantoine on 2007-10-24
In the package manager, look for a package named "compizconfig-settings-manager".  This will give you a great deal of options that you can use to tweak your compositor settings.

The icon for this tool will appear in System -> Preferences when installed.  It will also appear under System -> Preferences -> Appearance -> Visual Effects -> Custom, which incidentally is where you can turn off compiz if you prefer.

---

### Post by professor fate on 2007-10-24
> **FuturePilot said:**
> ```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```
That's your sound card. I also had no sound with that card. But you can easily get sound. Try [these]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")
instructions.

OK, I followed you link and did what it said, but I still don't have sound.  I used one of the example audio files that came with Ubuntu.  Suggestions?

---

### Post by FuturePilot on 2007-10-24
> **professor fate said:**
> OK, I followed you link and did what it said, but I still don't have sound.  I used one of the example audio files that came with Ubuntu.  Suggestions?

Did you reboot?

---

### Post by professor fate on 2007-10-24
> **FuturePilot said:**
> Did you reboot?

Yes, I rebooted, but the sound icon is muted and when I select it I get the following:

No volume control GStreamer plugins and/or devices found

---

### Post by jpittack on 2007-10-24
I saw that you have a dell 1390 wireless card.

[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

I have the same card, this works for me, and I don't have the same laptop described in the title.  Just the same wireless card.  Works on Gutsy, but the restricted drivers manager will have a solution for you.  Just know this will cut your speeds and reliability.

Do this following the install.  Be sure to follow what is not in the quote boxes, as these tell you what directory to be in.

---

### Post by professor fate on 2007-10-24
Hi,

I just got the wireless working, but you're right, the restricted drivers take a hit on speed.  Right now I'm dealing with sound.  

PF

---

### Post by jpittack on 2007-10-24
I totally understand your concern with sound.  Using the how to will help you get a better understanding of the terminal.  I don't know if you mentioned this yes, but are you using 64 bit or 32 bit?

---

### Post by quinnten83 on 2007-11-10
Is the professor stil having sound problems? I just would like to know (on account of the bet and all).

---

### Post by atomkarinca on 2007-11-10
AFAIK he worked it out. but you can check out [this thread]("http://ubuntuforums.org/showthread.php?t=589243") on how he solved his problem. it's a bit long read, though.

---

### Post by quinnten83 on 2007-11-10
I just finished reading the entire thing (and added a few comments while at it).
He did get it working, he also reinstalled a couple of times.
I think by now he is an expert and a professor.

---

