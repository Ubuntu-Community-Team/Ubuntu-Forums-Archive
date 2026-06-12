---
title: "iBook clamshell and &quot;melting&quot; video"
date: 2006-09-07
forum: Apple PPC Users
---

### Post by matei on 2006-09-07
Hi all,

I just tried to install Dapper on my iBook indigo clamshell.  Previous distros worked fine, however I'm having an issue installing Dapper.

It appears to install OK - however when X starts, the screen freezes and appears to "melt".  The sound works - and ctrl delete restarts X... but same behaviour.

Is there some way around this?  How can I get it to boot into a X-less session - if all else fails?

---

### Post by timbobsteve on 2006-09-08
Hi,

To get to a terminal you could boot off the install CD and mount your partitions then chroot into them to make changes.

It does sound like you will need to modify your XOrg configuration. Perhaps your color depth is incorrect (I experience similar problems when I use 24bit and not 16bit color)

The alternate installer CD is all CLI based so you can get to virtual terms to issue commands easier, but the desktop CD provides Terminal anyway so there is no difference really.

If the desktop CD works fine... then perhaps you should do the following from a Terminal from the live CD: (copy the Autoconfigured Xorg file from the Desktop CD to your HDD)

```
sudo mkdir /mnt/tmp
sudo mount /dev/hdaX /mnt/temp
sudo cp /etc/X11R6/xorg.conf /mnt/temp/etc/X11R6/           (*is it /etc/X11R6/ or /etc/X11/ ??)*
sudo umount /mnt/temp
```

Then just reboot. Hopefully that will fix any Xorg problems. If it isn't an XOrg problem then I am stuck. Hope that helps.

---

### Post by matei on 2006-09-09
Hi - thanks for the help.

It turned out to be the video settings.  Running the xorg reconfigure and setting it to 16-bit helped...  however, now Nautilus crashes out before Gnome can load up!

---

