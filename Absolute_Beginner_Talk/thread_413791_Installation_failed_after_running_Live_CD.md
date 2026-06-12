---
title: "Installation failed after running Live CD"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by idahogie on 2007-04-19
I am brand new to Linux, and thought I'd jump in at the deep end...I just bought a notebook from AVADirect with no OS installed.  Actually, they couldn't install either Fedora or SuSE Linux, so I had them ship it blank.  Here's the specs:

MICROSTAR, MSI MS-1042 (171772) Turion&#8482; 64 X2 Performance Notebook, 17" WXGA/WSXGA+ Glossy LCD, NVIDIA® GeForce&#8482; Go 7600 256MB Graphics 
AMD, Turion&#8482; 64 X2 TL-60 2.0GHz, Socket S1, 2x128KB L1 + 2x512KB L2 cache, 35W, 90nm, OEM 
CRUCIAL, 2GB (2 x 1GB) PC2-5300 DDR2 667MHz SDRAM SODIMM, CL5, Non-ECC 
HITACHI, 80GB Travelstar 7K100, 7200-RPM, 8MB cache, 9.5mm, SATA, OEM 
OPTICAL DRIVE, Super-Multi DVD±RW Optical Drive (Included) 
MICROSTAR, MP54GBT2 Combo Wireless-G + Bluetooth Adapter, IEEE 802.11b/g 11/54Mbps, MiniPCI (for MSI n/b only) 
LOGITECH, LX5 Cordless Optical Mouse, USB, PS2, Black 

I plugged in the Ubuntu Live CD (from *Ubuntu Linux Bible* by von Hagen) and it ran like a charm.  After a couple of tweaks, the wireless card was working, my mouse was working, I was playing around with the installed applications and games.  So then I thought to myself - might as well install it.

I used the desktop install icon, which was quick and painless.  But after rebooting, I get nothing.  I can't even boot from the Live CD anymore.  If I watch the boot sequence, the computer flashes something like 'Checking NVRAM...', then I get a flashing cursor on a blank screen.  It doesn't respond to anything I do.

I've played around in the BIOS, but I can't figure out what to tweak.  There was on option for 'Quick Boot.'  When that's enabled, I can at least shut the computer down with the power button.  If it's disabled, I have to pop the battery just to shut the thing down.

Sorry if this problem's been answered already.  I couldn't come up with a decent search criterion.

Thanks for any help.

---

### Post by markitect on 2007-04-19
id start with a bios reset to defaults just to be safe. 
You should also probably download a new 7.04 desktop disc and reinstall (im not sure what version come with your book)
If that doesn't work:

from the grub boot menu (you might have to hit esc to get to it)
press e over the ubuntu entry go down to the kernel line and press e again
add acpi=off to the end of the line.

my msi notebook has an acpi bug so i figure its a good place to start with yours.
Let us know if that lets you boot or not (if it does you can pop open a terminal and do a sudo edit /boot/grub/menu.lst and add the acpi=off to the kernel line in the first ubuntu entry)

but let us know if it succeeds because we will want to find out what specifically need to disable so that you can still have battery monitor and all that fun stuff.

---

### Post by idahogie on 2007-04-20
Thanks, Markitect.  This is such an active forum, and my post had spent three hours dropping like a stone with no response, that I had stopped paying attention.

Unfortunately, the BIOS reset didn't change anything.  And the machine will not boot.  It won't boot from the new install and it won't boot from the CD drive.  I downloaded the 7.04 AMD64 Ubuntu, but the drive will not read.  ESC does nothing.  The GRUB menu doesn't come up.  (I assume that's something that you get by hitting ESC during the boot process.)  It doesn't seem that there's any way to edit anything.

Anything else you can dredge up?

---

### Post by valberg on 2007-08-21
I've got exactly the same problem with a laptop with these specs:

AMD Turion dual core 64 bit 90nm, 800 MHz FSB, 1MB L2 cache, 1.6 GHz / 2.0 GHz
Nvidia Geforce Go 7600, 256MB RAM, PCI Express X16 bus
1024MB DDR2 RAM 200 pinn OEM
Harddrive SATA 2.5, 160.0GB 7200RPM
DVD RW Super Multi MSI

idahogie: have you have any luck with yours ?

I would really appreciate a answer :D since i've just bought the thing and kinda frustrated of it not working :S

---

### Post by TeaSwigger on 2007-08-21
"checking NVRAM" where NVRAM is NVideo card's RAM? Thus, video card problem, or perhaps more accurately, wrong graphics config somewhere in the boot stages? I don't know much about this stuff mind you, just trying to toss in a thought in the hopes it leads somewhere. Searched "checking NVRAM"?

---

### Post by valberg on 2007-08-21
well i can't find anywhere i can change the graphics for the boot stages... and searched NVRAM, just can't find any usefull stuff... :S

---

### Post by TeaSwigger on 2007-08-22
> **valberg said:**
> well i can't find anywhere i can change the graphics for the boot stages... and searched NVRAM, just can't find any usefull stuff... :S

Hopefully someone more knowledgeable than I will pitch in on this, but to toss in some more possible leads:

HOWTO: Change bootup and console resolution
[http://ubuntuforums.org/showthread.php?t=258484&highlight=set+resolution+boot+grub](http://ubuntuforums.org/showthread.php?t=258484&highlight=set+resolution+boot+grub)
Black screen and no usplash I figured it out!!!
[http://ubuntuforums.org/showthread.php?t=307700&highlight=set+resolution+boot+grub](http://ubuntuforums.org/showthread.php?t=307700&highlight=set+resolution+boot+grub)

But I'm not at all sure it's getting that far; sounds more like something in the boot sequence but I don't know much about that. Since it ran perfectly from the Live CD we do know that ubuntu can work the hardware fine. Sorry I can't help on that angle.

---

### Post by Wim Sturkenboom on 2007-08-22
My guess: NVRAM is **N**on **V**olatile RAM, so the battery backed memory where the BIOS stores its settings.

If your system does not want to boot from CD, check the boot sequence in the BIOS and make sure the CD is the first one.

---

