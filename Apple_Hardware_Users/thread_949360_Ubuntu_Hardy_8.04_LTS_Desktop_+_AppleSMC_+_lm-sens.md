---
title: "Ubuntu Hardy 8.04 LTS Desktop + AppleSMC + lm-sensors"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by kamimark on 2008-10-16
Hey guys,
I know this subject is being discussed a million times. Since I have been googling about it for half a week and found loads of posts. But since most of the posts are relatively old (2005-2007) I have a few questions.

First my goal. Increase the fan speed of my iMac 2006 (early) cause the Video Card is crashing.

Now according to my "research" i have found that there are several ways to do this.
One is using the applesmc module and configure the minimum fan speed to a higher value (same as smcFanControl app in MAC OSX).
However the folder where the file should exist for the minimum fan speed doesn't exist. No folder named applesmc or applesmc.XXX exist in /sys/devices/platform/

Also tried adding a line to /etc/sysctl.conf
devices.platform.applesmc.fan0_minimum_speed=5000

I also checked in the modules and applesmc seems to be loaded automatically.

Also tried to load applesmc module manually and I got some error which I don't remember. :)

Now the lm-sensors part.
After downloading all the related packages and doing a sensors-detect it detects only the Intel Core Duo temperature sensor.
So using sensors after reboot i can only see the temperatures.

The following info is from my unreliable memory :)
sensors-detect also detects something like "Trying SMC family - Yes. Unknown 0x00".

and dmesg outputs something like:
applesmc: wait status failed: c != 19

Also read some stuff about compiling a mac specific kernel but those posts were kind of old. I assume that Hardy generic can handle this right?

How can I achieve my goal? (installing MacOSX or Windows XP is not the answer I'm looking for :P)

Please help me. I wasted too much time on this...

---

### Post by Kooothor on 2008-10-16
> **kamimark said:**
> 
However the folder where the file should exist for the minimum fan speed doesn't exist. No folder named applesmc or applesmc.XXX exist in /sys/devices/platform/

Hi, 

If the folder applesmc doesn't show up in /sys/devices/plateform, try shutting down the computer completely, and then boot again.
If you boot into OSX and then reboot into linux, OSX messes with applesmc.
If you never had this folder, then I don't know.
But once you have /sys/devices/plateform/applesmc.768/fan1_min it's very easy to put in this file the fan speed you want.

But since the kernel update 2.6.24-21, I don't find this file anymore, but my fan is @ 4000 rpm (the speed I chose).


> **kamimark said:**
> 
Also tried adding a line to /etc/sysctl.conf
devices.platform.applesmc.fan0_minimum_speed=5000
Never heard about that.


> **kamimark said:**
> 
Now the lm-sensors part.
After downloading all the related packages and doing a sensors-detect it detects only the Intel Core Duo temperature sensor.
So using sensors after reboot i can only see the temperatures.

For lm-sensors, go on the website and download the latest perl script. then run it, it should detect more things.
and read this also  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119)

> **kamimark said:**
> 
and dmesg outputs something like:
applesmc: wait status failed: c != 19
I have these messages too. Don't know how to stop them.



I hope I helped you :)

Regards, 

~ktr

---

### Post by kosumi68 on 2008-10-16
> **kamimark said:**
> No folder named applesmc or applesmc.XXX exist in /sys/devices/platform/


This means applesmc is not loaded, or something went wrong. Check
```

lsmod | grep applesmc

```

If it is not there, do
```

sudo modprobe applesmc

```

No need to reboot the machine. If it fails, please report the error. Everything else you wrote depends on this error.

Regarding the sensor quality, you should get the updated applesmc from this thread: [http://ubuntuforums.org/showthread.php?t=924096&highlight=applesmc](http://ubuntuforums.org/showthread.php?t=924096&highlight=applesmc)

Make sure you are running the 2.6.24-19 kernel when testing (2.6.24-21 no supported yet).

---

### Post by kamimark on 2008-10-16
sensors-detect gives this as before

Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x0b00
> If the folder applesmc doesn't show up in /sys/devices/plateform, try shutting down the computer completely, and then boot again.
If you boot into OSX and then reboot into linux, OSX messes with applesmc.
Did it still same.
I dont have OSX anymore :)


Went to > [http://ubuntuforums.org/showthread.p...light=applesmc](http://ubuntuforums.org/showthread.p...light=applesmc)
updated the thing
now it seemed a bit better
since ```
sudo modprobe applesmc
``` doesn't give an error
```
lsmod | grep applesmc
``` shows it inside :)

 /sys/devices/platform/applesmc.768/ appeared.

changed the value and it worked.

But what's the deal with the lm-sensors?
I can't use it at all?

---

### Post by kosumi68 on 2008-10-16
> **kamimark said:**
> 
But what's the deal with the lm-sensors?
I can't use it at all?

I can't make much out of that error, which is supposed to set things up. However, did you try to run skip that and just run
```

sensors

```

---

### Post by cyberdork33 on 2008-10-16
> **kamimark said:**
> First my goal. Increase the fan speed of my iMac 2006 (early) cause the Video Card is crashing.

Now according to my "research" i have found that there are several ways to do this.
One is using the applesmc module and configure the minimum fan speed to a higher value (same as smcFanControl app in MAC OSX).
However the folder where the file should exist for the minimum fan speed doesn't exist. No folder named applesmc or applesmc.XXX exist in /sys/devices/platform/

Also tried adding a line to /etc/sysctl.conf
devices.platform.applesmc.fan0_minimum_speed=5000

I also checked in the modules and applesmc seems to be loaded automatically.

Also tried to load applesmc module manually and I got some error which I don't remember. :)

1. Please see the "Before you post" link in my signature to properly identify your iMac.
2. The applesmc module is really only for Macbooks.


> **kamimark said:**
> Now the lm-sensors part.
After downloading all the related packages and doing a sensors-detect it detects only the Intel Core Duo temperature sensor.
So using sensors after reboot i can only see the temperatures.
That's all that works on my iMac too.

You can still compile a custom kernel. That really hasn't changed. You can do that for any computer. You really don't need to though.

---

### Post by kosumi68 on 2008-10-16
There is a config for iMac in applesmc too, now. However, there are presumably several models unsupported so far. I you like, you could try running the scan-smc.sh script from this post:

[http://ubuntuforums.org/showthread.php?t=924096&highlight=applesmc&page=2](http://ubuntuforums.org/showthread.php?t=924096&highlight=applesmc&page=2)

and report the output here.

---

### Post by cyberdork33 on 2008-10-16
> **kosumi68 said:**
> There is a config for iMac in applesmc too, now. However, there are presumably several models unsupported so far. I you like, you could try running the scan-smc.sh script from this post:

[http://ubuntuforums.org/showthread.php?t=924096&highlight=applesmc&page=2](http://ubuntuforums.org/showthread.php?t=924096&highlight=applesmc&page=2)

and report the output here.

I will try that too. It has been awhile since I tried.

EDIT: Actually, it seems to work fairly well now for me... 

```
cyberdork33@Grover-Ubuntu:/sys/devices/platform/applesmc.768$ ls
driver       fan2_max     hwmon                     temp1_input
fan1_input   fan2_min     key_at_index              temp2_input
fan1_label   fan2_output  key_at_index_data         temp3_input
fan1_manual  fan2_safe    key_at_index_data_length  temp4_input
fan1_max     fan3_input   key_at_index_name         temp5_input
fan1_min     fan3_label   key_at_index_type         temp6_input
fan1_output  fan3_manual  key_count                 temp7_input
fan1_safe    fan3_max     modalias                  temp8_input
fan2_input   fan3_min     name                      temp9_input
fan2_label   fan3_output  power                     uevent
fan2_manual  fan3_safe    subsystem
```

Get a few errors from sensors though

```
cyberdork33@Grover-Ubuntu:/sys/devices/platform/applesmc.768$ sensors
applesmc-isa-0300
Adapter: ISA adapter
ODD :        801 RPM  (min =  800 RPM)
HDD :       1402 RPM  (min = 1400 RPM)
CPU :        863 RPM  (min =  800 RPM)
temp1:       +43.0°C                                    
temp2:       +33.0°C                                    
ERROR: Can't get value of subfeature temp3_input: I/O error
temp3:        +0.0°C                                    
temp4:       +52.0°C                                    
ERROR: Can't get value of subfeature temp5_input: I/O error
temp5:        +0.0°C                                    
temp6:       +45.5°C                                    
temp7:       +51.0°C                                    
temp8:       +41.5°C                                    
ERROR: Can't get value of subfeature temp9_input: I/O error
temp9:        +0.0°C   
```

---

### Post by kosumi68 on 2008-10-18
I managed to miss the attachment, but reading through it I see your model is not covered. Could you please provide the
```

sudo dmidecode | grep 'Product Name:'

```
and I'll add it for testing. One should not have to live with missing sensors anymore :-)

---

### Post by cyberdork33 on 2008-10-18
> **kosumi68 said:**
> I managed to miss the attachment, but reading through it I see your model is not covered. Could you please provide the
```

sudo dmidecode | grep 'Product Name:'

```
and I'll add it for testing. One should not have to live with missing sensors anymore :-)

The version # is in my signature ;) 

If you need more info than that, I will have to get it later since I am currently out of town and don't have access.

---

### Post by kosumi68 on 2008-10-19
> **cyberdork33 said:**
> The version # is in my signature ;) 


Bless you, cyberdork :-)

Ok, iMac5 it is. I attached the module source file here if you want to compile it yourself. Otherwise, with knowledge about which kernel version you run and which architecture, I can post a binary here for testing.

---

### Post by kosumi68 on 2008-10-20
Once there, running the test script from this post [http://ubuntuforums.org/showpost.php?p=5998563&postcount=53](http://ubuntuforums.org/showpost.php?p=5998563&postcount=53) ought to settle things.

I noticed your machine has a light sensor. Is it used for anything in particular on your machine?

---

### Post by cyberdork33 on 2008-10-20
> **kosumi68 said:**
> Once there, running the test script from this post [http://ubuntuforums.org/showpost.php?p=5998563&postcount=53](http://ubuntuforums.org/showpost.php?p=5998563&postcount=53) ought to settle things.

I noticed your machine has a light sensor. Is it used for anything in particular on your machine?

will do. I didn't know there was a light-sensor. I haven't noticed that it does anything... (OSX or otherwise).

---

### Post by cyberdork33 on 2008-10-21
Kernel Info
```
Linux Grover-Ubuntu 2.6.27-7-generic #1 SMP Fri Oct 17 22:24:30 UTC 2008 x86_64 GNU/Linux
```I think I figured out how to build and load the module though. log from test script attached. Light and LEDs are "not available".

Temps look good now though.

```
applesmc-isa-0300
Adapter: ISA adapter
ODD :        799 RPM  (min =  800 RPM)
HDD :       1399 RPM  (min = 1400 RPM)
CPU :        866 RPM  (min =  800 RPM)
temp1:       +30.5°C                                    
temp2:       +42.5°C                                    
temp3:       +44.0°C                                    
temp4:       +50.5°C                                    
temp5:       +43.5°C                                    
temp6:       +40.0°C                                    
temp7:       +49.2°C
```

---

### Post by kosumi68 on 2008-10-22
[http://lkml.org/lkml/2008/10/22/348](http://lkml.org/lkml/2008/10/22/348)

---

