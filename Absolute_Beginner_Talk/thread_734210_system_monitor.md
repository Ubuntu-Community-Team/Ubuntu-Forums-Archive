---
title: "system monitor"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by grumpylad77 on 2008-03-24
In system monitor, many of the processes show memory usage as:

17179869180.0 GB

There are 8 processes that always show that as memory usage

I know that it isn't right...(that would be a lot of RAM) but is there something that I may have done to make it show that?

---

### Post by herbster on 2008-03-24
Open a terminal and run

```
top
```

Still the same numbers? Paste what you see.

---

### Post by grumpylad77 on 2008-03-24
No, not the same..... here's what I got
 7335 mat       15   0  302m  77m  13m S    1  4.1   1:12.40 Xgl                
 7536 mat       15   0  244m  24m  12m S    1  1.3   0:01.76 gnome-terminal     
 7247 root      15   0  103m  12m 7108 S    1  0.7   0:06.81 Xorg               
 7440 mat       15   0  192m  18m 6276 S    1  1.0   0:04.16 compiz.real        
 7449 mat       15   0  144m 3272 1960 S    0  0.2   0:01.68 gnome-screensav    
 7556 mat       15   0 18948 1324  972 R    0  0.1   0:00.49 top                
    1 root      18   0  5112 1968  572 S    0  0.1   0:01.21 init               
    2 root      14  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.07 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.04 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 


Must just be something with the system monitor

---

### Post by herbster on 2008-03-24
The gnome-system-monitor is definitely off. Did you close it and run it again? And are you sure you saw what you saw? ;) Just double and triple check things like this.

---

### Post by grumpylad77 on 2008-03-24
Yep, just checked again...

When I first open system monitor, everything is normal. About 1-2 seconds after it opens, those same processes 

-Emerald
-Firefox Bin
-Gnome Panel
-Gnome-system-monitor
-mixer_applet2
-multiload-applet2
-nautilus
-trash applet

same processes every time
-

---

### Post by herbster on 2008-03-24
Okay, but is there still a problem you need resolving? Is gnome-system-monitor still reporting those memory usage sizes? Can you take a screenshot of it? Use Gimp, File > Acquire > Screenshot of window, set a 2 second delay or something and click on the gnome-system-monitor window when the cursor changes to the cross and attach the image.

---

### Post by grumpylad77 on 2008-03-24
Here it is.....

---

### Post by herbster on 2008-03-24
Definitely a read error. Try logging out and back in, if it shows the same numbers, try rebooting. That should all but certainly resolve it.

---

### Post by grumpylad77 on 2008-03-24
Logged out and back in with no change.

Rebooted and still no change.....

still those same 8 processes

---

### Post by herbster on 2008-03-24
Boom: [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/148325](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/148325)

She's a bug.

---

### Post by grumpylad77 on 2008-03-24
Ok, thanks for the help.....:)

---

