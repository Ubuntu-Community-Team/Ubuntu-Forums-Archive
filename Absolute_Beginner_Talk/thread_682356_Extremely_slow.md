---
title: "Extremely slow"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2008-01-29
I have a very old laptop and the specs are somewhat like this

8100 - P III 600 Mhz, 20 GB HDD, 256 MB RAM , 2.5 MB Video card(NeoMagic). No ethernet port (using a PCMCIA card for ethernet).

Trouble is that Xubuntu 7.10 is extremely slow on the machine. I had installed Zenwalk prior to Xubuntu and it worked quite well. 

I switched to Xubuntu only because I was very familiar to the package management system in Xubuntu, having used Ubuntu since Breezy. Also the number of apps available are much more than in Zenwalk.

It is so slow that I have to wait for the letters to appear on the display whenever I type something. And this is not only in browsers. It happens even in the terminal.

Can someone tell me what could be the problem. Zenwalk didnt have this problem. :(

I'd really like to keep Xubuntu but if its going to be this slow then I might just have to change back to Zenwalk.

Here's a snapshot of my top :
```
 Tasks:  98 total,   4 running,  89 sleeping,   0 stopped,   5 zombie
Cpu(s): 23.2%us,  3.0%sy,  0.0%ni, 63.9%id,  7.0%wa,  3.0%hi,  0.0%si,  0.0%st
Mem:    255876k total,   250320k used,     5556k free,     5256k buffers
Swap:   498004k total,   107512k used,   390492k free,    78448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4663 root      15   0  294m  25m 6340 R 20.5 10.4  14:49.30 Xorg               
12343 inxsible 15   0  204m  61m  22m S  4.0 24.6   3:59.23 firefox-bin        
11974 inxsible 15   0 74048  18m 9508 R  0.7  7.5   0:04.76 xfce4-terminal     
12466 inxsible 15   0  2360 1136  876 R  0.3  0.4   0:00.13 top                
    1 root      15   0  2948  512  460 S  0.0  0.2   0:03.13 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.12 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.15 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   26 root      13  -5     0    0    0 S  0.0  0.0   0:00.13 kblockd/0          
   42 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   75 root      15   0     0    0    0 S  0.0  0.0   0:00.56 pdflush            
   76 root      15   0     0    0    0 S  0.0  0.0   0:00.68 pdflush            
   77 root      10  -5     0    0    0 S  0.0  0.0   0:03.26 kswapd0            
  128 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0   
```

---

### Post by smartboyathome on 2008-01-29
I would recommend installing server and then installing only what you want, or possibly trying Fluxbuntu.

---

### Post by asmoore82 on 2008-01-30
this might not help but it couldn't hurt...
you could make double sure that the composite graphics extension to Xorg is disabled.

edit your xorg.conf with root privilege: ```
gksu gedit /etc/X11/xorg.conf
```(you may have to use a text editor different from `gedit` for Xubuntu)

and add these lines to the very bottom of the file:
```
Section "Extensions"
	Option	    "Composite" "0"
EndSection
```
restart(either just X or the whole OS) for the change to take effect and see it that helped.

---

### Post by JoshuaRL on 2008-01-30
Use nano or mousepad instead of gedit.

---

### Post by asmoore82 on 2008-01-30
> **JoshuaRL said:**
> Use nano or mousepad instead of gedit.
thanks for the clarification; I'm not very familiar with Xubuntu.
use `sudo` instead of `gksu` if you are going to use `nano`
since it is text based.

---

### Post by Inxsible on 2008-01-30
That simply starts Xubuntu in low graphics mode. Asks to login to CLI mode and then  again in X. 

Does not even take up the entire screen space. The max resolution available was 640x480,  although it did make the keyboard more responsive.

I changed that back to the way it was.

---

### Post by Inxsible on 2008-01-30
This is a standard Xubuntu install with gnome services initiated at startup. No KDE services are initiated at startup.

Are there any unnecessary processes that I can kill to do something with the responsiveness of the computer?

---

### Post by asmoore82 on 2008-01-30
that shouldn't have happened...
could you post your xorg.conf file?

---

### Post by JoshuaRL on 2008-01-30
What type of video card do you have?  I think that's the problem.  I think it has you in the vesa driver, which runs all that through the processor.  And since you have a pretty slow one, it make everything slow.

---

### Post by kerry_s on 2008-01-30
make sure you change your xorg.conf from the usual "vesa" to "neomagic". debian would be faster on that old rig( [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso) )
to get the fastest you would want to do a debian custom install build up( [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso) )
install the base, that means uncheck all the packages in package selection stage
log in as root
apt-get install xorg gdm synaptic (what ever else)
(example mine: apt-get install xorg gdm synaptic jwm emelfm leafpad iceweasel)
reboot(ctrl+alt+delete)

jwm is a ultra small wm, not the easist to learn, but worth it.

if all else fails, xp can run very nicely when trimmed, let me know if you need a link. :lolflag: i'm on xp right now so->

---

### Post by Inxsible on 2008-01-30
> **JoshuaRL said:**
> What type of video card do you have?  I think that's the problem.  I think it has you in the vesa driver, which runs all that through the processor.  And since you have a pretty slow one, it make everything slow.

Its not vesa. I had checked that earlier. Its savage.

---

### Post by Inxsible on 2008-01-30
> **asmoore82 said:**
> that shouldn't have happened...
could you post your xorg.conf file?
Here's my xorg
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "S3 Inc. 86C270-294 Savage/MX-MV"
    Driver        "savage"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "S3 Inc. 86C270-294 Savage/MX-MV"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

```

---

### Post by Inxsible on 2008-01-30
> **kerry_s said:**
> make sure you change your xorg.conf from the usual "vesa" to "neomagic". debian would be faster on that old rig( [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso) )
to get the fastest you would want to do a debian custom install build up( [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso) )
install the base, that means uncheck all the packages in package selection stage
log in as root
apt-get install xorg gdm synaptic (what ever else)
(example mine: apt-get install xorg gdm synaptic jwm emelfm leafpad iceweasel)
reboot(ctrl+alt+delete)

jwm is a ultra small wm, not the easist to learn, but worth it.

if all else fails, xp can run very nicely when trimmed, let me know if you need a link. :lolflag: i'm on xp right now so->I was hoping I wouldn't have to go the minimal install route. But if thats what it takes, then that's what it takes.

Zenwalk does seem a lot more responsive though. I might just end up using that. I just didnt quite like the Netpkg in Zenwalk.

---

### Post by kerry_s on 2008-01-30
try the debian xfce4, you should find it faster than xubuntu and might be faster then zenwalk. 
[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso)

you only need to go custom if your out for the speed. your specs are good enough you can run most things, it's just a matter of what your after. you can even run DSL( [http://damnsmalllinux.org/](http://damnsmalllinux.org/) ) in ram for the most speed. your cpu is better than mine and i've made all kinds of setups work, you should be able to get exactly what you want.

---

### Post by Inxsible on 2008-01-30
I'll give debian xfce a go. I am not looking to do some high end graphics on this dino here...but at least I don't expect it to be so slow that I have to literally wait for the words to show up once I type them.

---

### Post by Jay Jay on 2008-01-30
> I have a very old laptop and the specs are somewhat like this

8100 - P III 600 Mhz, 20 GB HDD, 256 MB RAM , 2.5 MB Video card(NeoMagic). No ethernet port (using a PCMCIA card for ethernet).

Trouble is that Xubuntu 7.10 is extremely slow on the machine. I had installed Zenwalk prior to Xubuntu and it worked quite well. 

My "Linux laptop" has a similar spec to yours - same CPU speed and RAM...

>  It is so slow that I have to wait for the letters to appear on the display whenever I type something. And this is not only in browsers. It happens even in the terminal.

I'd really like to keep Xubuntu but if its going to be this slow then I might just have to change back to Zenwalk.


You're not alone. This happens to me regularly too, especially whilst using IM programs such as aMSN. During conversations I often have to wait for the OS to "catch up" with my typing lol. At other times I've witnessed bouts of slowdown. Last night it took 10 mins for The Gimp to open. Last year I migrated from Kubuntu 7.04 after experiencing these problems. Other users advised me to run Xubuntu Gutsy instead to resolve the slowdown but this issue hasn't gone away totally.

A poster on here has reported that Xubuntu 7.04 provides better performance for older machines than the newer 7.10, I'm going to give this a go and see for myself.

> your cpu is better than mine and i've made all kinds of setups work, you should be able to get exactly what you want.

What speed is your CPU and did you have any success with coaxing Kubuntu to work well on machines of our spec? I'd be interested in your findings... 

Jay

---

### Post by kerry_s on 2008-01-30
> Quote:
your cpu is better than mine and i've made all kinds of setups work, you should be able to get exactly what you want.
What speed is your CPU and did you have any success with coaxing Kubuntu to work well on machines of our spec? I'd be interested in your findings...

Jay

mines 450mhz 256ram, i didn't like kubuntu, but kde runs just fine. if you want you can try the debian kde version it's alot faster than kubuntu and none of the stuff is missing/hidden from konqueror, like it is in kubuntu.-> [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-kde-CD-1.iso)


also i keep forgetting, you can also try debian from live cd, won't be as fast but you can see what you'll get first before you decide to wipe your current os.->
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)
[http://live.debian.net/cdimage/monthly-builds/current/i386/](http://live.debian.net/cdimage/monthly-builds/current/i386/)

---

### Post by Jay Jay on 2008-02-02
Thanks for the information, I'll check those versions out. FWIW, I've gone back to Xubuntu 7.04 and it definitely feels much faster than 7.10 in day to day usage.

---

### Post by walmartshopper67 on 2008-02-02
I cant really tell if this does anything, but i've noticed that if you raise the the nice level of xorg really high - like  -20 it seems to go a lot smoother. the command is renice -20 $(pidof X) replace -20 with whatever level you want between  -1 and -20 (need to be root/sudo)

also there's a program called "Auto Nice Daemon" - it essentially polls the system and nices processes to a set level based on their priority and cpu usage. that could help i think.

---

