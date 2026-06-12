---
title: "Brand Spankin' New Nvidia drivers"
date: 2012-04-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by monk0nuggets on 2012-04-11
Alright.  Today Nvidia finally released drivers for their GeForce 635m cards (which now come standard in Asus N55s).  I was hoping to finally get my Nvidia card up and running within Linux, but it seems I don't know enough about how to install these new drivers.

I thought I had the current common Nvidia drivers in place (they are downloaded and installed), but when I check to see what driver is running it says it is the Intel® Sandybridge Mobile.  I tried nvidia-xconfig, but it says command not found.  Nvidia settings loads up, but tells me to run xconfig.

My knowledge on this has run dry.  Your help would be much appreciated.

---

### Post by monk0nuggets on 2012-04-13
Alright, so the daily Ubuntu update included the new driver in the package, but my computer still is not recognizing that it exists.

---

### Post by watersevenub on 2012-04-13
I have a N55S running 12.04 with latest nvidia-current which supports G635M and I am having exactly the same issues.

---

### Post by watersevenub on 2012-04-13
This command returns a different model.

sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: GF106 [GeForce GT 555M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom

---

### Post by monk0nuggets on 2012-04-13
Mine says this:
*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom*-display

---

### Post by watersevenub on 2012-04-16
You should have two graphic cards listed. Do,
sudo lshw -c video | more

---

### Post by monk0nuggets on 2012-04-17
This is what I got this time:

*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0

---

### Post by chugtairizwan on 2012-04-17
Thnk GOD! i was waiting for this :)

---

### Post by monk0nuggets on 2012-10-09
It seems that my previous post was with a bit of over excitement, missing the fact that my specific card was not covered in the update.  This time though, I'm quite sure that my card is covered.  The newest driver looks to have been released about two weeks ago.

[http://www.nvidia.com/object/linux-display-amd64-304.51-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.51-driver.html)

---

