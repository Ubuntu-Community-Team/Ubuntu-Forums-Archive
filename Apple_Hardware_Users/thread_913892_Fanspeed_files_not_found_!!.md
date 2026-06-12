---
title: "Fanspeed files not found !!"
date: 2008-09-08
forum: Apple Hardware Users
---

### Post by Kooothor on 2008-09-08
Hey folks, 

I need some help before my macbook burns !! :D

Everything used to be fine, my fan used to go at 3000 RPM
But this morning I accidently booted into osX, and now with the command "sensors" I can't get any fanspeed output !
The cause is certainly because I have no more fan* files into my /sys/devices/platform/applesmc.768/ folder....

and I can't create them as I see :  No such file or directory

HELP pls !

a ls -a of this applesmc.768 directory shows this :
```
ls -a
.          key_at_index              modalias      temp1_input  temp7_input
..         key_at_index_data         name          temp2_input  temp8_input
calibrate  key_at_index_data_length  position      temp3_input  temp9_input
driver     key_at_index_name         power         temp4_input  uevent
hwmon      key_at_index_type         subsystem     temp5_input
input      key_count                 temp10_input  temp6_input
```

Any help appreciated !

---

### Post by cyberdork33 on 2008-09-08
try completely shutting down the machine and then turning it back on, instead of 'restarting'. Sometimes the state of variables and hardware can be set by OS X, and they are not cleared unless the machine is completely powered down.

---

### Post by Kooothor on 2008-09-08
You were right cyberdork !!!
Thank you so much :D

I've shutted down the machine completely and then rebooted directly into Linux and my fanspeed files reappeared :)

Also I remember now that this morning when I booted into linux after osx, I had a gnome error...

---

