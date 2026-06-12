---
title: "Mini DisplayPort and Samsung SyncMaster 2433"
date: 2010-01-19
forum: Apple Hardware Users
---

### Post by acoliver on 2010-01-19
I have a MacBook Pro 5,2 with the Mini-DisplayPort for external video.  I have the displayport-VGA adapter which works (albeit sometimes at an unideal resolution) with an array of projectors, LCDs and other stuff.  Everything except for my nice Samsung SyncMaster 2433.  When I plug it in, I get the weird rainbow screwed up look with only the far left hand column looking normal and the rest looking like I've got the wrong refresh rate or something.  However, the same setup works when I boot from Karmic to OS X.  Note this also didn't work in Jaunty.  Any idea why this happens?

I'm using the NVidia 185.18.36.  

Oddly...
It also did not work through a KVM switch (long shot) but oddly the "Monitor Out" works when I run this monitor through my Dell projector.  if I unplug the projector and then plug the monitor in directly without rescanning for displays, the monitor continues to work.

---

### Post by acoliver on 2010-02-04
After manually upgrading to the 190.53 driver from the nvidia website ([http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html)), my problems are resolved.  The display works perfectly with the adapter/monitor.

---

