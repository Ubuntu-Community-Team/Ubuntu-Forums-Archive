---
title: "Compiz Problem, intel graphics card"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by tdashroy on 2008-01-24
When I run compiz it says the following:

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

I was wondering if somebody could possibly englight me as to what this means and how I can go about fixing it.  Thanks a ton.

---

### Post by RomeReactor on 2008-01-24
Hi. Please open a terminal (Applications->Accessories->Terminal) and run:
```
sudo lshw -C display
```
and post the output; if you have an Intel 965, then it's blacklisted on the [Compiz wiki]("http://wiki.compiz-fusion.org/Hardware/Blacklist").

Try editing the configuration file for Compiz:
```
gksudo gedit ~/.config/compiz/compizconfig/config
```
and add this line at the bottom:
```
SKIP_CHECKS=yes
```
save the file, close the text editor, then press CTRL+ALT+BACKSPACE to restart your display.

---

### Post by tdashroy on 2008-01-24
*-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


That is the output I get, so I believe that does mean I have a 965.  But, I don't even have a compiz directory in my .config.

---

### Post by RomeReactor on 2008-01-24
Yes, your card is a 965:
> **tdashroy said:**
> *-display:0             
       description: VGA compatible controller
       product: Mobile **GM965**/GL960 Integrated Graphics Controller

Press ALT+F2 and try running this:
```
SKIP_CHECKS=yes compiz
```
or:
```
SKIP_CHECKS=yes compiz.real
```

---

### Post by tdashroy on 2008-01-25
Okay I ran both of those, but when I run the first one I get the error:

Could not open location 'file:///SKIP_CHECKS=yes compiz'
The location or file could not be found.

And when I run the compiz.real one all I get is firefox opening up to the default page...
Btw thank you for helping me

---

### Post by RomeReactor on 2008-01-25
You might want to wait until Hardy is released; the reason the 965 is blacklisted is due to problems with video playback that are now [being solved in Hardy]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/148247"), though it's not quite fixed yet. Otherwise, try opening the Compiz script in Gedit:
```
gksudo gedit /usr/bin/compiz
```
Scroll down to line 56 and you should see this section:
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
[B]T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)[/B]
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```
Note the two lines in bold. Try commenting out these two lines by adding a **#** sign at the beginning of each line, so they look like this:
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
[B]# T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
# T="$T 8086:2972" # i965 (x3000)[/B]
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```
Save the file, close the text editor and restart your display by pressing CTRL+ALT+BACKSPACE; log in again, and see if you can enable the effects now.

---

### Post by tdashroy on 2008-01-25
Still nothing...could this possibly be the reason why whenever I start my computer it says it is running in low graphics mode and I have to configure to the correct graphics card drivers?

---

