---
title: "PPC - Life with Hardy on 20&quot; G5 iMac"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by stream303 on 2008-04-26
For the most part, Hardy is running ok on my PPC G5 iMac, and here are some notes:

Installation from an "alternate" image went smoothly, and I dedicated the whole internal disk to Xubuntu, and let guided partitioning do all the hard work. :)

The fans screamed, but only during install, and after the first reboot, they operated as normal quietly.  A dev is working on fixing this installation issue possibly being incorporated in the next spin, 8.04.1.  Again, after the first reboot the fans are ok.

At the first reboot, I noticed that my screen stayed in black with just a blinking cursor until the gdm login screen appeared.  I fixed that problem by using this at the second-stage boot: prompt

```
Linux nosplash
```

Since that worked, I added that to the append= line of /etc/yaboot.conf, then sudo ybin -v -C /etc/yaboot.conf to make the system aware of the change and tada - boot messages now scroll by on startup.

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash fb=false"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="nosplash fb=false"
```

Actually, I also added fb=false to my kernel parameters too as I found it sped up the display a bit as well.

Make the system aware of the change:
```
sudo ybin -v -C /etc/yaboot.conf
```

Note that on a 20" G5 iMac with the opensource nvidia driver, there is a shifting-bug that has been with us since Gutsy - it is coming way upstream from freedesktop.org and is being looked into.  The bug is that the display is shifted about a 1/2 inch to the right, and wraps back around to the left side.  Annoying, but not a showstopper.  I look forward to seeing a fix trickle back down through the distros.

Cpu frequency scaling with powernowd does not work out of the box.  I had to uninstall powernowd, and use an alternate scaler, **CPUDYN**, which I just downloaded via synaptic.  Great - now it normally toggles between power save 900mhz, and performance at 1.8ghz.  Someday I'll try to work on powernowd and see if I can't get it to use "ondemand", but cpudyn is performing admirably for now.

Screen resolution was detected on my nvidia card with no problem at 1680x1050.  However, even though my screen is large, it still isn't quite the quality of an Apple Cinema display.  Therefore, I chose to add the "FPDither" "true" option to my /etc/X11/xorg.conf file to have it dither.  Fine details look much better at the small cost of processing - I hardly notice any delays.

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Option          "FPDither" "true"**
EndSection
```

I use this option on ALL my machines that have nvidia cards and lcd displays, and find that it makes the screen much more precise.  YMMV.

I am running Xubuntu 8.04 and really like it, especially since the iMac doesn't really have a hardware screen brightness control (the devs are working on that too), so I can fake it a bit by using Xubuntu's brightness control a little bit.

Also, since I am coming from an RC, I think my /etc/apt/sources.list file may not be optimal, even after manually editing it to reflect the fact that we are now using ubuntu-ports, rather than the main archives.  Therefore, my repositories show up as "3rd-party" rather than being on the main source tab.  Those I have left UNchecked for now, as leaving them checked in the main repositories makes them look for the old standard archives, which are no longer populated with our ported software.

Whew...  any more questions, just ask!

---

