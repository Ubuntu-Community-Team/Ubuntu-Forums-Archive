---
title: "VGA problem when loading Edgy - flashing bars"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by SinoDave on 2006-10-31
When I installed 6.06 on my notebook, I had no strange video issues on boot. It displayed the box to let me know it was loading the kernel and correctly adjusted the resolution and refresh rates so that all loading notification messages were displayed correctly.

When I installed 6.10 (both Ubuntu and Kubuntu), I get the same video problem when the installer loads and whenever the system boots: after I make my GRUB selection, the screen fills with flashing vertical bars. They remain there until the system adjusts the resolution/refresh rate to enter the desktop and displays the login screen. In Gnome, this caused other video problems as well (especially in causing the text behind loading bars to be completely illegible), but with KDE the problems end with the desktop load. When I reboot or shutdown the system, I get the same flashing bars until all processes are finished and the the machine powers down or flashes the BIOS screen.

I can't understand why 6.10 would do this when 6.06 did not. Is there any way to adjust the VGA settings for boot? There doesn't seem to be a choice to adjust anything on the GRUB menu like there is on the CD installer. BTW, when I installed from the CD, the install menu displayed correctly so I didn't mess with any VGA settings, but the flashing bars came up immediately after selecting Install/boot from CD.

This is more of an annoyance at the moment, but since legible displays during this time, if there is an error or a message that requires user input, I will be unable to do anything. I would like to resolve this if possible.

Thanks everyone for your help.

FYI I am using an ancient (five-year-old) Acer Travelmate 612TXC and I'm not 100% sure of the graphics chip involved, but of course I could research that if necessary

---

### Post by matthewv on 2006-11-01
The solution to this **should** be very simple. When grub loads, highlight the menu entry you wish to boot, and hit 'e' to edit it. Highlight the line that says 'kernel' at the start, and then press 'e' to edit that line. At the very end of the line, add vga=771 , then hit enter to save the change and 'b' to boot. If this works, you can make the change permanent by editing /boot/grub/menu.lst (as root, eg Alt-F2, then 'sudo gedit /boot/grub/menu.lst') and add vga=771 at the end of the appropriate line (somewhere near the bottom).

The reason this occurs in edgy and not in dapper is that usplash, the program that produces this splash screen, received significant upgrades, including the ability to scale to much higher resolutions. Unfortunately, there are still a few problems.

---

### Post by SinoDave on 2006-11-01
> **matthewv said:**
> The solution to this **should** be very simple. When grub loads, highlight the menu entry you wish to boot, and hit 'e' to edit it. Highlight the line that says 'kernel' at the start, and then press 'e' to edit that line. At the very end of the line, add vga=771 , then hit enter to save the change and 'b' to boot. If this works, you can make the change permanent by editing /boot/grub/menu.lst (as root, eg Alt-F2, then 'sudo gedit /boot/grub/menu.lst') and add vga=771 at the end of the appropriate line (somewhere near the bottom).

The reason this occurs in edgy and not in dapper is that usplash, the program that produces this splash screen, received significant upgrades, including the ability to scale to much higher resolutions. Unfortunately, there are still a few problems.

Actually, I fixed it, but not in the way you said. When I added that text to the end of the line, I got a message the it was not a supported mode and I had to select from a list of 8 or so modes. The ones that I tried all netted the same results.

In the end, the solution was in editing the /etc/usplash.conf file and changing the xres and yres values from 1024x768 to 800x600. My notebook supports 1024x768, but apparently not at the refresh rate that usplash was trying to display. Everything looks great now.

Thanks for your help and the push in the right direction.

---

