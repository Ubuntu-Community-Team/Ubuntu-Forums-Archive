---
title: "Problem booting Mac Pro 5,1 with linux kernel 6.8.0 – no problems with 6.5"
date: 2024-08-30
forum: Apple Hardware Users
---

### Post by cliverlong2 on 2024-08-30
*Cross-posted on stack exchange Ask Different and Macrumors forums*

I am running a MacPro 5,1 which can triple boot MacOS Sonoma, Ventura and Ubuntu/Linux from separate SSDs. In the past two days I could not boot Linux 6.8.0. MacOS and Linux 6.5.0 boot fine.

I use OpenCore Legacy patcher (OCLP) on the MP 5,1 to select the required boot drive (each OS on separate SSD).

I do the following to attempt to boot Linux

Select the Linux boot drive from OCLP menu.
When screen clears press ESC once.
The Grub 2.06 menu appears
Select Advanced options
Two Linux kernels, and recover mode, appear for selection on GRUB2 menu

1) If I select linux 6.8.0-40-generic and press ESC to display boot message the boot gets to various points then hangs. A regular sequence of messages includes: Mounting bootefi, … Finished load kernel module efi-pstore. At this point the boot does not proceed , the machine hangs for about 30 seconds then the screen goes blank.

The fans ramp up speed for 2 seconds then stop and the machine just displays a blank screen. I have to press the power button for about 5 seconds to switch off the machine.

2) If I select linux 6.5.0-45-generic the machine boots fully, I can sign on and all attached screens display.

3) If I select linux 6.8.0-40-generic (recovery mode) the machine boots fully, I can sign on and one attached screen displays – the other screens are blank.

Any suggestions on how I diagnose and fix the 6.8.0-40 boot problem? I can work perfectly fine with 6.5.0 but the boot process is inconvenient.

The oclp forum suggests I post in a Linux forum because as Linux starts to boot, OCLP has completed its job successfully. 

Thanks
cliverlong

---

### Post by QIII on 2024-08-30
Moved to **Apple Hardware Users**

---

### Post by cliverlong2 on 2024-09-04
**Information below cross-posted on : Ask Different, MacRumors Apple hardware, Ubuntu forum**

I think the problem maybe to do with video card support. The MacPro 5,1 has a RX580 installed. 
I have installed Linux Ubuntu 24.04.1 on an SSD in a USB caddy and I can attempt to boot from it 

1. When running Linux Ubuntu 22.04.4, kernel 6.5.0-45 or MacOS Ventura or Sonoma, the RX580 video card can drive 3 displays all extended to one logical desktop.

2.  When running Linux Ubuntu 22.04.4, kernel 6.8.0-40 or Linux Ubuntu 24.04.1, kernel 6.8.0-41 boot hangs at message &#8220;Reached target local-fs&#8221;, the screen goes blank and the keyboard becomes unresponsive.

2.1 If I power off two of the displays the Linux boot still hangs at message &#8220;Reached target local-fs&#8221; as above.

3. If I boot Ubuntu 22.04.4, Ubuntu 24.04.1 in recovery mode then Linux will boot into Gnome graphical but only display one screen.

4. I can successfully boot a Windows laptop using the Ubuntu 24.04.1 USB disk. The laptop has only the built-in screen.

From what I can see, something changed between Linux kernel  6.5.0-45 and 6.8.0-40 where booting a MacPro 5,1 with a video card which can attach multiple displays - maybe the problem is present in any video card with the chipset in the RX580.

---

