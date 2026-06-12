---
title: "Screen Resolution at 640 x 480"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by oberg on 2007-11-09
I recently installed Ubuntu 7.10 and it used to work perfectly fine.  I went into my screen resolutions and manually selected what graphics card I had because I figured I should.  Once I did this the next time I logged in my screen resolution was stuck at 640 x 480.  I don't know how to get it back.  

Please help.

---

### Post by oberg on 2007-11-09
when running: 
```
sudo lshw -C display
```

i get:

description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8

please help.

---

### Post by oberg on 2007-11-09
I fixed it, ignore post.

---

### Post by unrepper on 2007-11-09
I have the same issue.  Could you explain how you fixed it?

---

