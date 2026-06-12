---
title: "Installed vmware player, but no sound"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-04-24
I just installed vmware player using "add/remove programs" and it all installed without error, but when I started a virtual machine,  it failed to connect to the sound device. It was looking for /dev/dsp. 

Is this the right device name?  
Any ideas on how I can fix it?

---

### Post by ubnewbie2 on 2007-04-24
Seems the problem was Firefox (or one of it's plugins) was holding the /dev/dsp device open.  Closing Firefox enabled vmware to access the device.

Is there any way to make Firfox share /dev/dsp, or at least relinquish it after a timeout?

---

