---
title: "screen blanking issue"
date: 2012-04-27
forum: Any Other OS
---

### Post by hollowhead on 2012-04-27
This an issue I had in maverick but I'm posting here since I switched to mint 12 partly because this issue and partly to escape unity.  The problem is my screen blanks soon after boot.  The mouse shape changes when I move it over the screen so it is not technically a crash, but the system is unusable since it doesn't unblank.  I have to hit the power button.  After about 5 minutes after startup it won't happen.  If the xscreensaver starts it usually doesn't happen, also keeping the system busy usually helps for those first few minute.  I'm using MATE but it happened under ubuntu gnome classic and mint gnome 3. It also sometimes happens at the login screen.  It has been suggested its a graphics issue and since it doesn't happen on my daughter's laptops running exactly the same operating system this makes sense.  Can anyone help I had to restart 3 times this morning?

```

inxi -F
System:    Host nrh1-Satellite-L350 Kernel 3.0.0-12-generic i686 (32 bit) Desktop N/A Distro Linux Mint 12 Lisa
Machine:   System TOSHIBA (portable) product Satellite L350 version PSLD4E-008004EN
           Mobo TOSHIBA model Portable PC version Base Board Version Bios INSYDE version 2.00 date 08/11/2009
CPU:       Dual core Celeron CPU T3000 (-MCP-) cache 1024 KB flags (lm nx sse sse2 sse3 ssse3) 
           Clock Speeds: (1) 1796.097 MHz (2) 1796.097 MHz
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller 
           X.Org 1.10.4 drivers intel unloaded: fbdev,vesa Resolution 1440x900@59.9hz 
           GLX Renderer Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 GLX Version 2.1 Mesa 7.11
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver HDA Intel Sound: ALSA v: 1.0.24
Network:   Card Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver r8169 
           IF: eth0 state: down speed: 10 Mbps duplex: half mac: 00:1e:33:fd:5f:82
Drives:    HDD Total Size: 250.1GB (14.7% used) 1: /dev/sda TOSHIBA_MK2555GS 250.1GB 
Partition: ID:/ size: 115G used: 5.4G (5%) fs: ext4 ID:/home size: 111G used: 30G (28%) fs: ext4 
           ID:swap-1 size: 5.06GB used: 0.00GB (0%) fs: swap 
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes 139 Uptime 54 min Memory 357.5/1883.8MB Client Shell inxi 1.7.7 



```

```

inxi -F
System:    Host nrh1-Satellite-L350 Kernel 3.0.0-12-generic i686 (32 bit) Desktop N/A Distro Linux Mint 12 Lisa
Machine:   System TOSHIBA (portable) product Satellite L350 version PSLD4E-008004EN
           Mobo TOSHIBA model Portable PC version Base Board Version Bios INSYDE version 2.00 date 08/11/2009
CPU:       Dual core Celeron CPU T3000 (-MCP-) cache 1024 KB flags (lm nx sse sse2 sse3 ssse3) 
           Clock Speeds: (1) 1796.097 MHz (2) 1796.097 MHz
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller 
           X.Org 1.10.4 drivers intel unloaded: fbdev,vesa Resolution 1440x900@59.9hz 
           GLX Renderer Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 GLX Version 2.1 Mesa 7.11
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver HDA Intel Sound: ALSA v: 1.0.24
Network:   Card Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver r8169 
           IF: eth0 state: down speed: 10 Mbps duplex: half mac: 00:1e:33:fd:5f:82
Drives:    HDD Total Size: 250.1GB (14.7% used) 1: /dev/sda TOSHIBA_MK2555GS 250.1GB 
Partition: ID:/ size: 115G used: 5.4G (5%) fs: ext4 ID:/home size: 111G used: 30G (28%) fs: ext4 
           ID:swap-1 size: 5.06GB used: 0.00GB (0%) fs: swap 
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes 139 Uptime 54 min Memory 357.5/1883.8MB Client Shell inxi 1.7.7 
nrh1@nrh1-Satellite-L350:~$ inxi -Gx
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org 1.10.4 drivers intel unloaded: fbdev,vesa Resolution 1440x900@59.9hz 
           GLX Renderer Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 GLX Version 2.1 Mesa 7.11 Direct Rendering Yes


```

---

### Post by OpenSourceRules on 2012-04-28
Have you tried Cinnamon?

---

### Post by hollowhead on 2012-04-28
I'm not sure I've found the whole gnome/cinnamon issue difficult to understand since I switched to mint I did an install on my root partition and kept home.  I seemed to end with something when I logged in using gnome that was some kind of unique fusion, what I had didn't match the description of cinnamon or gnome 3.  But my feeling is is quite a fundamental bug since it happened in maverick and all mint variants I can choose.  Thanks for the reply.

---

### Post by The Rnegade on 2012-05-02
> **hollowhead said:**
> This an issue I had in maverick but I'm posting here since I switched to mint 12 partly because this issue and partly to escape unity.  The problem is my screen blanks soon after boot.  The mouse shape changes when I move it over the screen so it is not technically a crash, but the system is unusable since it doesn't unblank.  I have to hit the power button.  After about 5 minutes after startup it won't happen.  If the xscreensaver starts it usually doesn't happen, also keeping the system busy usually helps for those first few minute.  I'm using MATE but it happened under ubuntu gnome classic and mint gnome 3. It also sometimes happens at the login screen.  It has been suggested its a graphics issue and since it doesn't happen on my daughter's laptops running exactly the same operating system this makes sense.  Can anyone help I had to restart 3 times this morning?

```

inxi -F
System:    Host nrh1-Satellite-L350 Kernel 3.0.0-12-generic i686 (32 bit) Desktop N/A Distro Linux Mint 12 Lisa
Machine:   System TOSHIBA (portable) product Satellite L350 version PSLD4E-008004EN
           Mobo TOSHIBA model Portable PC version Base Board Version Bios INSYDE version 2.00 date 08/11/2009
CPU:       Dual core Celeron CPU T3000 (-MCP-) cache 1024 KB flags (lm nx sse sse2 sse3 ssse3) 
           Clock Speeds: (1) 1796.097 MHz (2) 1796.097 MHz
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller 
           X.Org 1.10.4 drivers intel unloaded: fbdev,vesa Resolution 1440x900@59.9hz 
           GLX Renderer Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 GLX Version 2.1 Mesa 7.11
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver HDA Intel Sound: ALSA v: 1.0.24
Network:   Card Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver r8169 
           IF: eth0 state: down speed: 10 Mbps duplex: half mac: 00:1e:33:fd:5f:82
Drives:    HDD Total Size: 250.1GB (14.7% used) 1: /dev/sda TOSHIBA_MK2555GS 250.1GB 
Partition: ID:/ size: 115G used: 5.4G (5%) fs: ext4 ID:/home size: 111G used: 30G (28%) fs: ext4 
           ID:swap-1 size: 5.06GB used: 0.00GB (0%) fs: swap 
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes 139 Uptime 54 min Memory 357.5/1883.8MB Client Shell inxi 1.7.7 



``````

inxi -F
System:    Host nrh1-Satellite-L350 Kernel 3.0.0-12-generic i686 (32 bit) Desktop N/A Distro Linux Mint 12 Lisa
Machine:   System TOSHIBA (portable) product Satellite L350 version PSLD4E-008004EN
           Mobo TOSHIBA model Portable PC version Base Board Version Bios INSYDE version 2.00 date 08/11/2009
CPU:       Dual core Celeron CPU T3000 (-MCP-) cache 1024 KB flags (lm nx sse sse2 sse3 ssse3) 
           Clock Speeds: (1) 1796.097 MHz (2) 1796.097 MHz
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller 
           X.Org 1.10.4 drivers intel unloaded: fbdev,vesa Resolution 1440x900@59.9hz 
           GLX Renderer Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 GLX Version 2.1 Mesa 7.11
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver HDA Intel Sound: ALSA v: 1.0.24
Network:   Card Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver r8169 
           IF: eth0 state: down speed: 10 Mbps duplex: half mac: 00:1e:33:fd:5f:82
Drives:    HDD Total Size: 250.1GB (14.7% used) 1: /dev/sda TOSHIBA_MK2555GS 250.1GB 
Partition: ID:/ size: 115G used: 5.4G (5%) fs: ext4 ID:/home size: 111G used: 30G (28%) fs: ext4 
           ID:swap-1 size: 5.06GB used: 0.00GB (0%) fs: swap 
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes 139 Uptime 54 min Memory 357.5/1883.8MB Client Shell inxi 1.7.7 
nrh1@nrh1-Satellite-L350:~$ inxi -Gx
Graphics:  Card: Intel Mobile 4 Series Chipset Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org 1.10.4 drivers intel unloaded: fbdev,vesa Resolution 1440x900@59.9hz 
           GLX Renderer Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 GLX Version 2.1 Mesa 7.11 Direct Rendering Yes


```

it sounds like a hardware or driver problem to me. make sure you have all the proper drivers installed, and that your hardware meets the minimum hardware requirements

---

