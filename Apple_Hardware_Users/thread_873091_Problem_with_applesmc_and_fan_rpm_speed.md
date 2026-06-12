---
title: "Problem with applesmc and fan rpm speed"
date: 2008-07-28
forum: Apple Hardware Users
---

### Post by 74141 on 2008-07-28
Hi,

First at all, I am gald to be here.

I have a MacBook santa rosa machine (v 3.1), and this is the first time I using ubuntu on it, before that I was using openSUSE 10.3 and 11.0, and I like to say, ubuntu it 's so friendly with my machine, and my Apple Wireless Keyboard :)

The only problem that I have it, is with fan rpm speed, I try using applesmc and make it speedup at 3000 rpm, because my machine temperature it's looks like higher a little bit, and the fans working some time at maximize rpm speed, so after I loading the muodule applesmc, and try to speedup the fan rpm, I had this message:
```
su
# echo 3000 > /sys/devices/platform/applesmc.768/fan1_min
bash: /sys/devices/platform/applesmc.768/fan1_min: No such file or directory

```
The same problem if I trying to do it with sudo!

any Idea to fix this?

I 'm using ubuntu hardy 8.04.1 32bit.

Thanks, and sorry for my bad English language, it 's not my mother language.

---

### Post by cyberdork33 on 2008-07-28
Can you navigate to that directory and see if the folder even exists?

```
cd /sys/devices/platform/applesmc.768
ls
```

---

### Post by 74141 on 2008-07-28
cyberdork33:

This is the output after I shutdown my machine:
```
calibrate    hwmon                     modalias      temp3_input
fan1_input   input                     name          temp4_input
fan1_label   key_at_index              position      temp5_input
fan1_manual  key_at_index_data         power         temp6_input
fan1_max     key_at_index_data_length  subsystem     temp7_input
fan1_min     key_at_index_name         temp10_input  temp8_input
fan1_output  key_at_index_type         temp1_input   temp9_input
fan1_safe    key_count                 temp2_input   uevent
bx@MacBook:/sys/devices/platform/applesmc.768$ 

```

OK, I found the solution:
> This happens to me as well, some of the time. I see the following pattern: if I reboot from OS X, the fan files are missing. If I do a shutdown on OS X, then boot to ubuntu, they exist. If I reboot Ubuntu, they exist.

This is a MacBook Santa Rosa, 32 bit hardy heron, and the precompiled kernel from linux-image-2.6.24-18-generic. I'm loading applesmc in /etc/modules. I'll provide more information if necessary. Right now I'm good with always doing a shutdown on OS X.
Now it is works!
this make me confuse a little bit :confused:
---

Another question please :)
How can I make the fan speed at 3000 rpm by default?
And is there any possible to make bluetooth service working after I waking up my machine from suspend? the same question with fan rpm speed.

Big Thanks to cyberdork33, for your fast replay :)

---

### Post by cyberdork33 on 2008-07-28
> **74141 said:**
> OK, I found the solution:

Now it is works!
this make me confuse a little bit :confused:
---

Another question please :)
How can I make the fan speed at 3000 rpm by default?
And is there any possible to make bluetooth service working after I waking up my machine from suspend? the same question with fan rpm speed.

Big Thanks to cyberdork33, for your fast replay :)
Ok that explains it. I will try to remember that in the future. Macs act weird about some of the hardware. I assume that rebooting from OSX leaves the fan controller variables in place and they cannot be accessed by something new until they lose power. Something similar happens with the iSight.

you can add that echo command to a script that executes on startup... probably rc.local would work.

The suspend issue is another problem altogether. Basically, modules do not get reloaded after resuming from suspend. I am not sure of how to remedy this.

---

### Post by 74141 on 2008-07-28
> The suspend issue is another problem altogether. Basically, modules do not get reloaded after resuming from suspend. I am not sure of how to remedy this.
Thank you.

Actually, In openSUSE 10.3, I was searched about it and I found that I should add a command to file that make bluetooth service starting after I waking up my machine, in this bath:
```
/etc/pm/config.d/modules
```

So I decide to testing it with ubuntu right now, and this what I do:
```
sudo gedit /etc/pm/config.d/modules
```

add:
service bluetooth start
Save it, than close.

Try it by suspend the system, and wake it up, and it's works! :)

---

### Post by 74141 on 2008-07-28
By the way, I installed debian-helper-scripts before that, to make starting services easier to me :)

---

