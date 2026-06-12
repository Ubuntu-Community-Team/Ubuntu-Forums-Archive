---
title: "Shutdown not completing cleanly on Ubuntu 22.04"
date: 2023-05-11
forum: Apple Hardware Users
---

### Post by smnbldwn on 2023-05-11
I recently did a clean install of Ubuntu 22.04 on my 2008 MacBook 4.1 and then installed the old Ubuntu Unity desktop. (I actually like Unity and am prepared to take the performance hit compared to a lighter desktop.)

OS: Ubuntu 22.04.2 LTS x86_64 
Host: MacBook4,1 1.0 
Kernel: 5.19.0-41-generic 
Uptime: 18 mins 
Packages: 2138 (dpkg), 10 (flatpak), 
Shell: bash 5.1.16 
Resolution: 1280x800 
DE: Unity 7.6.0 
WM: Compiz 
WM Theme: Yaru-dark 
Theme: Yaru-dark [GTK2/3] 
Icons: ubuntu-mono-dark [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel Core 2 Duo T8300 (2) @ 2.4 GHz 
GPU: Intel Mobile GM965/GL960 
Memory: 1579MiB / 3903MiB 


Everything works great except that when I shut it down, the shutdown doesn't complete. This issue also happens with the standard desktop.
If I choose verbose shutdown so I can see what is going on, the process completes without error and the screen goes black but the fans remain running and the white light on the front illuminates if I close the lid. I have to then hard shutdown by holding the power button down for 5s.


Does anyone have any tips to force a complete shutdown on this hardware? Just in case its relevant, reboot works

---

### Post by smnbldwn on 2023-05-11
I solved it by adding acpi=force to the grub configuration.

1) [HTML]sudo nano /etc/default/grub[/HTML]
2) Add acpi=force to the GRUB_CMDLINE_LINUX_DEFAULT line e.g.[HTML]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"[/HTML]
3) [HTML]sudo update-grub[/HTML]

And now it shuts down cleanly!

[COLOR=#333333][FONT=&quot]

[/FONT][/COLOR]

---

