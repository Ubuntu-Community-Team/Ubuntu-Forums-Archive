---
title: "How install video driver?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-07-21
Absolute Linux newbie.  I have a Dell laptop that uses an XGI Volari XP5 video card, which is a Trident card, I believe.

I'm currently using the default Vesa driver, and it generally runs fine, except for choppy video playback, and slow running of Google Earth (it tells me I'm running in emulation mode or something.)

My question is how do I update the video driver?  Can I use a generic Trident driver?

Xorg.conf shows
Section "Device"
    Identifier    "Generic Video Card"
    Driver        "vesa"
    BusID        "PCI:1:0:0"
EndSection


I think I've downloaded a Trident driver package, but I don't know what to do with it.  A Locate for Trident gets me
bill@Laptop:~$ locate trident
/var/lib/dpkg/info/xserver-xorg-driver-trident.list
/var/lib/dpkg/info/xserver-xorg-driver-trident.md5sums
/lib/modules/2.6.15-23-386/kernel/drivers/video/tridentfb.ko
/lib/modules/2.6.15-23-386/kernel/sound/oss/trident.ko
/lib/modules/2.6.15-23-386/kernel/sound/pci/trident
/lib/modules/2.6.15-23-386/kernel/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.15-23-386/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.15-25-386/kernel/drivers/video/tridentfb.ko
/lib/modules/2.6.15-25-386/kernel/sound/oss/trident.ko
/lib/modules/2.6.15-25-386/kernel/sound/pci/trident
/lib/modules/2.6.15-25-386/kernel/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.15-25-386/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.15-26-386/kernel/drivers/video/tridentfb.ko
/lib/modules/2.6.15-26-386/kernel/sound/oss/trident.ko
/lib/modules/2.6.15-26-386/kernel/sound/pci/trident
/lib/modules/2.6.15-26-386/kernel/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.15-26-386/kernel/sound/pci/trident/snd-trident.ko
/usr/lib/dri/trident_dri.so
/usr/lib/xorg/modules/drivers/trident_drv.so
/usr/share/doc/xserver-xorg-driver-trident
/usr/share/doc/xserver-xorg-driver-trident/changelog.Debian.gz
/usr/share/doc/xserver-xorg-driver-trident/copyright
/usr/share/man/man4/trident.4.gz

Any help would be appreciated.

Thanks,
eKennedy

---

### Post by adam.tropics on 2006-07-21
the simple way to find out is to try it!

In a terminal, do,

```
sudo dpkg-reconfigure xserver-xorg
```

and follow through, defaults are mostly fine but select the trident driver from the list it gives you. Make a note of the above command, and restart x or reboot. If all is well, it will start gnome/kde, else it will give you a text login, from where you will need to re-run the above command and select vesa again, followed by 

```
startx
```

---

### Post by uzd4ce on 2006-07-22
Thanks for the help.  Reconfigured xorg.conf for the Trident driver and it didn't work.  Was able to change it back, so I guess I'll just live with the Vesa driver until I get a different laptop.

Thanks again.

---

