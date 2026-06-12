---
title: "[SOLVED] MPB4,1/MBA 'wait status failed: c != 8' solved?"
date: 2008-09-19
forum: Apple Hardware Users
---

### Post by kosumi68 on 2008-09-19
UPDATE 12DEC2011: Since FEB2011, most Macbook models should work out of the box, without patching the kernel. If you experience problems or suspect your machine is different somehow, please read on.

UPDATE 28APR2010: For the latest applesmc, see the applesmc-dkms package in the Mactel PPA: [https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

If you have a Mac that is yet unsupported by applesmc, please reply to this post, gathering the information below.

* Determine your exact mac model
```

sudo dmidecode -s system-product-name

```

* Run the applesmc-test.sh script (found below in this post) to get a picture of the performance before the patch
```

./applesmc-test.sh

```
(you may need to do 'chmod +x ./applesmc-test.sh' before it runs)

* Run the scan-smc.sh script (found below in this post), and attach the output.
```

sudo ./scan-smc.sh > scan-smc-MODEL.txt

```
(you may need to do 'chmod +x ./scan-smc.sh' before it runs)

After some time, a reply with a new version of applesmc-dkms attached will appear. Then please run applesmc-test.sh again. Once satisfactory, the change will be incorporated in the Mactel PPA, and a patch sent upstream.

For more information, see [http://bitmath.org/code/applesmc-dkms/](http://bitmath.org/code/applesmc-dkms/)

---

### Post by cyberdork33 on 2008-09-19
It might be helpful if there was a test app or something that could verify the functions. Do you know if there is one or maybe a procedure for testing with stuff that is available?

---

### Post by cyberdork33 on 2008-09-19
Have you seen any of this?
[http://www.phoronix.com/scan.php?page=news_item&px=NjcyOA](http://www.phoronix.com/scan.php?page=news_item&px=NjcyOA)

---

### Post by kosumi68 on 2008-09-19
> **cyberdork33 said:**
> Have you seen any of this?
[http://www.phoronix.com/scan.php?page=news_item&px=NjcyOA](http://www.phoronix.com/scan.php?page=news_item&px=NjcyOA)

Well, the patches referred to are from me, and today they made it to Andrew Morton's mm tree, so I guess I have seen it :-) Not this link though, thanks for the tip.

Cheers,
Henrik

---

### Post by kosumi68 on 2008-09-19
> **cyberdork33 said:**
> It might be helpful if there was a test app or something that could verify the functions. Do you know if there is one or maybe a procedure for testing with stuff that is available?

I did not fully understand what you mean here, but if you think of a script that checks the availability of accelerometer, backlight, leds, fans, temperatures etc, that could be quite handy. However, currently the testing is about whether this works at all for some machines, which is easily verified by the number of errors in dmesg from applesmc.

---

### Post by cyberdork33 on 2008-09-19
> **kosumi68 said:**
> Well, the patches referred to are from me, and today they made it to Andrew Morton's mm tree, so I guess I have seen it :-) Not this link though, thanks for the tip.

Cheers,
HenrikThought so ;) I thought you'd like to see your work on phoronix.

> **kosumi68 said:**
> I did not fully understand what you mean here, but if you think of a script that checks the availability of accelerometer, backlight, leds, fans, temperatures etc, that could be quite handy. However, currently the testing is about whether this works at all for some machines, which is easily verified by the number of errors in dmesg from applesmc.
Actually, I don't know of anything that uses the accelerometer... backlight should work with pommed, and the fan control files can be seen in the dev tree. You have a good point on the messages though.

---

### Post by kosumi68 on 2008-09-20
EDIT 28APR2010: see first post in thread for current script versions [old version deleted].

On request, here is a small script that can be run to test the performance of applesmc on your computer. Simply run it in a terminal as a normal user. Cheers!

---

### Post by kosumi68 on 2008-09-21
Binary for Intrepid running 2.6.27-3-generic on i386 available, see the first post.

---

### Post by _mario_ on 2008-09-21
Hi,

thanks for figuring out how to get basic support. The 'c != 8'-problem seems to be solved ;-), but there are other issues on a MacBookPro 4 (Penryn):
```

Sep 21 21:38:07 snoopy kernel: [12118.120999] applesmc: Apple MacBook Pro detected:
Sep 21 21:38:07 snoopy kernel: [12118.121007] applesmc:  - Model with accelerometer
Sep 21 21:38:07 snoopy kernel: [12118.121010] applesmc:  - Model with light sensors and backlight
Sep 21 21:38:07 snoopy kernel: [12118.121014] applesmc:  - Model with 12 temperature sensors
Sep 21 21:38:07 snoopy kernel: [12118.121739] applesmc: device has already been initialized (0xe0, >
Sep 21 21:38:07 snoopy kernel: [12118.121743] applesmc: device successfully initialized.
Sep 21 21:38:07 snoopy kernel: [12118.122039] applesmc: 2 fans found.
Sep 21 21:38:07 snoopy kernel: [12118.127281] input: applesmc as /devices/platform/applesmc.768/inp>
Sep 21 21:38:07 snoopy kernel: [12118.163212] Registered led device: smc::kbd_backlight
Sep 21 21:38:07 snoopy kernel: [12118.163257] applesmc: driver successfully loaded.
Sep 21 21:38:07 snoopy kernel: [12118.169154] applesmc: light sensor data length set to 6
[tons of:]
Sep 21 21:39:03 snoopy kernel: [12130.824745] applesmc: wait status failed: 5 != 0
[... and sometimes:]
Sep 21 21:39:04 snoopy kernel: [12131.267745] applesmc: wait status failed: 5 != 1
Sep 21 21:46:49 snoopy kernel: [12268.875983] applesmc: wait status failed: 5 != 4

```
while running your test script:
```

accelerometer: present, readable, output: (2,10,233)
fan:           present, readable, output: 1000
light:         present, readable, output: (15,44)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           readable, output: 44750
 temperature:           readable, output: 35000
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 33750
 temperature:           readable, output: 51000
 temperature:           readable, output: 48500
 temperature:           readable, output: 50250
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 49750
 temperature:           readable, output: 42500
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      16

```

Probably due to errors reading non-existent temperature sensors (how many does this model have?).

But light sensors, keyboard backlight and fan speeds seems to work most of the time, although the GNOME applet sometimes complains about missing data/unreadable fan speeds.

ciao,
Mario

---

### Post by _mario_ on 2008-09-21
those temperature sensors not readable are: 1, 6, 7, 12 and the sensors command shows:
```

applesmc-isa-0300
Adapter: ISA adapter
Left side  : 999 RPM  (min = 1000 RPM)
Right side : 996 RPM  (min = 1000 RPM)
temp2:       +33.8°C                                    
temp3:       +51.2°C                                    
temp4:       +49.2°C                                    
temp5:       +51.2°C                                    
temp8:       +50.2°C                                    
temp9:       +42.5°C                                    
temp10:      +44.8°C                                    
temp11:      +35.0°C                                    

```

---

### Post by kosumi68 on 2008-09-21
_mario_,

thanks for the report! I have a comment, a question and a script:

1. Occasional read errors are quite natural, given that there is a finite probability (p) for every read to fail (and it will stay that way unless the applesmc sensor interface introduces buffered reading). The probability of *all* 12 sensors being ok in a read is (1-p)^12, which quickly becomes small if p is only slightly greater than zero.

2. The diagnostics suggests some sensors truly are not readable, but to make sure, one can try reading a single value, like
```

cat /sys/devices/platform/applesmc.768/temp1_input

```

3. To make sure exactly what sensors are there, try running the attached script as root (courtesy of Nicolas Boichat).

---

### Post by cyberdork33 on 2008-09-21
> **kosumi68 said:**
> 1. Occasional read errors are quite natural, given that there is a finite probability (p) for every read to fail (and it will stay that way unless the applesmc sensor interface introduces buffered reading). The probability of *all* 12 sensors being ok in a read is (1-p)^12, which quickly becomes small if p is only slightly less than unity.
free stats lesson today... :)

---

### Post by _mario_ on 2008-09-22
> **kosumi68 said:**
> 
2. The diagnostics suggests some sensors truly are not readable, but to make sure, one can try reading a single value.


Yes, as stated in my previous post the sensors 1, 6, 7 & 12 are always not readable.

> **kosumi68 said:**
> 
3. To make sure exactly what sensors are there, try running the attached script as root (courtesy of Nicolas Boichat).


I attached the output of this command. Btw: What does this mean? Is there any documentation one can read?

thanks & ciao,
Mario

---

### Post by kosumi68 on 2008-09-22
> 
I attached the output of this command. Btw: What does this mean? Is there any documentation one can read?


Great! The sensors list shows that MBP4,1 has 12 sensors, but four of them have different names from the older MBPs, precisely the ones you reported as failing. I will submit a patch for it shortly.

Documentation? :-) This script was given to me by the applesmc maintainer. Together with the kernel code, it is about the extent of what I know. There might be some general documentation regarding the sensor codes out there, but Apple-specific details are few and far between.

---

### Post by kosumi68 on 2008-09-22
_mario_,

Please find enclosed a patch to fix the temperature sensor list on MBP4,1, and a precompiled 2.6.27-3-generic i386 binary including that patch.

Hope this helps!

---

### Post by _mario_ on 2008-09-22
> **kosumi68 said:**
> 
Please find enclosed a patch to fix the temperature sensor list on MBP4,1, and a precompiled 2.6.27-3-generic i386 binary including that patch.
Hope this helps!
Thanks. I applied the patch to the source file and compiled myself, so now it seems to work:
```

performance:   reading all temperatures
 fail frequency:        .262
 reads per second:      71
```
and:
```

applesmc-isa-0300
Adapter: ISA adapter
Left side  :1006 RPM  (min = 1000 RPM)
Right side :1002 RPM  (min = 1000 RPM)
temp1:       +31.8°C                                    
temp2:       +50.0°C                                    
temp3:       +47.5°C                                    
temp4:       +53.0°C                                    
temp5:       +49.5°C                                    
temp6:       +70.0°C                                    
temp7:       +38.5°C                                    
temp8:       +48.5°C                                    
temp9:       +41.0°C                                    
temp10:      +42.0°C                                    
temp11:      +43.8°C                                    
temp12:      +33.5°C
```
There are still some messages left (as you already pointed out) we shouldn't be concerned about:
```

Sep 22 15:35:01 snoopy kernel: [ 1468.433884] applesmc: wait status failed: 5 != 0
Sep 22 15:35:01 snoopy kernel: [ 1468.460291] applesmc: wait status failed: 5 != 1
```
I asked for documentation to better understand how this chip works, and to get to know which temperature sensor is where inside the machine...

ciao,
Mario

---

### Post by kosumi68 on 2008-09-22
> **_mario_ said:**
> 
```

performance:   reading all temperatures
 fail frequency:        .262
 reads per second:      71

```


Excellent, I will send the patch to kernel.org.

Thanks!

PS. I am switching this thread to solved - always wanted to do that :-P

---

### Post by _mario_ on 2008-09-29
Hi again,

maybe we should also change the SYSFS directory from /sys/class/leds/smc::kbd_backlight to /sys/class/leds/smc:kbd_backlight. At least this is where pommed (version 1.16~mactel1) searchs the files. Or is it some bug in pommed? What is right? The current stable upstream kernel version still uses the former path.

ciao,
Mario

---

### Post by cyberdork33 on 2008-09-29
> **_mario_ said:**
> Hi again,

maybe we should also change the SYSFS directory from /sys/class/leds/smc::kbd_backlight to /sys/class/leds/smc:kbd_backlight. At least this is where pommed (version 1.16~mactel1) searchs the files. Or is it some bug in pommed? What is right? The current stable upstream kernel version still uses the former path.

ciao,
Mario
the mactel compile is old. Try this one:
[http://packages.debian.org/lenny/pommed](http://packages.debian.org/lenny/pommed)

---

### Post by kosumi68 on 2008-09-29
Not only did the name change from leds/smc:kbd_backlight to leds/smc::kbd_backlight as you noticed, but it lately (intrepid) changed to leds:smc::kbd_backlight... Somewhat confusing.

Btw, with the help of Bob McElrath, the applesmc reading errors have lately been further improved; I am attaching the latest version for Intrepid (applesmc.c.zip at the bottom). To get a version usable in Hardy, simply apply the trivial patch below.

Cheers!

```

--- upstream-2.6/drivers/hwmon/applesmc.c       2008-09-29 17:50:30.000000000 +0200
+++ hardy/drivers/hwmon/applesmc.c      2008-09-27 17:07:33.000000000 +0200
@@ -565,7 +565,7 @@ static ssize_t applesmc_light_show(struc
                ret = applesmc_get_key_type(LIGHT_SENSOR_LEFT_KEY, query);
                if (ret)
                        goto out;
-               data_length = clamp_val(query[0], 0, 10);
+               data_length = query[0];
                printk(KERN_INFO "applesmc: light sensor data length set to "
                        "%d\n", data_length);
        }
@@ -951,7 +951,7 @@ static ssize_t applesmc_key_at_index_sto
 }
 
 static struct led_classdev applesmc_backlight = {
-       .name                   = "smc::kbd_backlight",
+       .name                   = "smc:kbd_backlight",
        .default_trigger        = "nand-disk",
        .brightness_set         = applesmc_brightness_set,
 };

```

---

### Post by kosumi68 on 2008-10-09
All patches to applesmc are in Intrepid kernel 2.6.27-6.9-20, meaning they will appear in the next kernel release. They will also appear upstream in 2.6.28.

---

### Post by kosumi68 on 2008-10-25
Support for the latest Macbooks can from now on be found in the applesmc-dkms package in the mactel PPA: [http://ubuntuforums.org/showpost.php?p=6027135&postcount=143](http://ubuntuforums.org/showpost.php?p=6027135&postcount=143)

---

### Post by AleXit on 2008-11-05
Hello,
I've Intrepid on a Macbook4,1. 
I've installed applesmc-dkms package as suggested, but I get this:
```
ale@MacBook:~$ dmesg | grep applesmc
[   18.117779] applesmc: Apple MacBook detected:
[   18.117783] applesmc:  - Model with accelerometer
[   18.117785] applesmc:  - Model without light sensors and backlight
[   18.117787] applesmc:  - Model with 10 temperature sensors
[   18.121107] applesmc: device has already been initialized (0xe0, 0x00).
[   18.121109] applesmc: device successfully initialized.
[   18.121910] applesmc: 1 fans found.
[   18.125350] input: applesmc as /devices/platform/applesmc.768/input/input13
[   18.160105] applesmc: driver successfully loaded.
[   20.806727] applesmc: wait status failed: 5 != 0
[   20.842791] applesmc: wait status failed: 5 != 0
[   26.833031] applesmc: wait status failed: 5 != 0
[   56.154154] applesmc: wait status failed: 5 != 0
[   56.191405] applesmc: wait status failed: 5 != 0
[  291.957947] applesmc: wait status failed: 5 != 0
[  291.994704] applesmc: wait status failed: 5 != 0
(and so on)
```
This is the result of the script:
```
ale@MacBook:~/Desktop$ ./applesmc-test.sh 
accelerometer: present, readable, output: (-12,5,270)
fan:           present, readable, output: 2024
light:         not present
leds:          not present
temperatures:  present,
 temperature:           not readable
 temperature:           readable, output: 30250
 temperature:           readable, output: 51750
 temperature:           readable, output: 49000
 temperature:           readable, output: 52250
 temperature:           readable, output: 48250
 temperature:           not readable
 temperature:           readable, output: 49750
 temperature:           readable, output: 49250
 temperature:           readable, output: 49000
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      12
```
Does applesmc-dkms support my mac model?
Thanks!

---

### Post by kosumi68 on 2008-11-05
> **AleXit said:**
> Hello,
I've Intrepid on a Macbook4,1.
[...]
Does applesmc-dkms support my mac model?
Thanks!

Check the last post in this thread: [http://ubuntuforums.org/showthread.php?t=964840](http://ubuntuforums.org/showthread.php?t=964840)

---

### Post by calebio on 2008-11-07
> **kosumi68 said:**
> On request, here is a small script that can be run to test the performance of applesmc on your computer. Simply run it in a terminal as a normal user. Cheers!

Here is the output of this script for my iMac6,1:
```
accelerometer: not present
fan:           present, readable, output: 600
light:         not present
leds:          not present
temperatures:  present,
 temperature:           readable, output: 129000
 temperature:           readable, output: 25500
 temperature:           readable, output: 50000
 temperature:           readable, output: 60750
 temperature:           readable, output: 50250
 temperature:           readable, output: 48500
 temperature:           not readable
 temperature:           readable, output: 41500
 temperature:           not readable
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      13
```

---

### Post by kosumi68 on 2008-11-07
> **calebio said:**
> Here is the output of this script for my iMac6,1:


Great. Would you like to also report the output of 'sudo scan-smc.sh', please? The script is here: [http://ubuntuforums.org/attachment.php?attachmentid=85996&d=1224442499](http://ubuntuforums.org/attachment.php?attachmentid=85996&d=1224442499).

Thanks!

---

### Post by calebio on 2008-11-08
> **kosumi68 said:**
> Great. Would you like to also report the output of 'sudo scan-smc.sh', please? The script is here: [http://ubuntuforums.org/attachment.php?attachmentid=85996&d=1224442499](http://ubuntuforums.org/attachment.php?attachmentid=85996&d=1224442499).

Thanks!

Attached. It's all greek to me....

---

### Post by kosumi68 on 2008-11-08
> **calebio said:**
> Attached. It's all greek to me....

Here is a package with support for iMac6. Please run the test script again, and post the output here. If you want to appear in the kernel logs as Tested-by, send me a private message with name and email. Thanks!

---

### Post by calebio on 2008-11-08
> **kosumi68 said:**
> Here is a package with support for iMac6. Please run the test script again, and post the output here. If you want to appear in the kernel logs as Tested-by, send me a private message with name and email. Thanks!

Oh, hey, look at that! More and better output:
```
accelerometer: not present
fan:           present, readable, output: 600
light:         not present
leds:          not present
temperatures:  present,
 temperature:           readable, output: 63250
 temperature:           readable, output: 26500
 temperature:           readable, output: 129000
 temperature:           readable, output: 41500
 temperature:           readable, output: 129000
 temperature:           readable, output: 58000
 temperature:           readable, output: 47500
 temperature:           readable, output: 47000
 temperature:           readable, output: 46000
 temperature:           readable, output: 37000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      83
```

---

### Post by kosumi68 on 2008-11-09
> **calebio said:**
> Oh, hey, look at that! More and better output:


Great! Here is the upstream patch: [http://lkml.org/lkml/2008/11/9/93](http://lkml.org/lkml/2008/11/9/93)

---

### Post by dxlr8r on 2008-11-11
My Mac Pro:
```
dmidecode -s system-product-name
MacPro3,1

```

Nothing with applesmc works. When I try to modprobe it it says:
```
modprobe applesmc
FATAL: Error inserting applesmc (/lib/modules/2.6.27-7-generic/kernel/drivers/hwmon/applesmc.ko): No such device]
```

But the file IS there :)

```
sudo applesmc-test.sh'
accelerometer:[: 23: /sys/devices/platform/applesmc.768/position: unexpected operator
 not present
fan:          [: 38: /sys/devices/platform/applesmc.768/fan1_output: unexpected operator
 not present
light:        [: 53: /sys/devices/platform/applesmc.768/light: unexpected operator
 not present
leds:          not present
temperatures:  not present
performance:    not performed

```

```
sudo scan-smc.sh
cd: 7: can't cd to /sys/devices/platform/applesmc.768/
/home/simen/Desktop/scan-smc.sh: 60: let: not found
/home/simen/Desktop/scan-smc.sh: 60: let: not found
/home/simen/Desktop/scan-smc.sh: 60: let: not found
/home/simen/Desktop/scan-smc.sh: 60: let: not found
/home/simen/Desktop/scan-smc.sh: 60: let: not found
/home/simen/Desktop/scan-smc.sh: 60: let: not found
... Continues into infinity

```

---

### Post by kosumi68 on 2008-11-11
> **dxlr8r said:**
> My Mac Pro:
```
dmidecode -s system-product-name
MacPro3,1

```


Attached is a debian package that should recognize your machine as a MacPro, so that testing can begin. :-)

---

### Post by dxlr8r on 2008-11-12
Will it work with Ubuntu 32 bit? I'm planning on installing 32 bit since I do alot of 32 bits compiling. Especially with Wine since I use Linux to play games, since I don't do Windows...

---

### Post by kosumi68 on 2008-11-12
> **dxlr8r said:**
> Will it work with Ubuntu 32 bit? 

By design, DKMS packages work for all kernel versions and all architectures.

---

### Post by cyberdork33 on 2008-11-12
> **kosumi68 said:**
> By design, DKMS packages work for all kernel versions and all architectures.

It essentially compiles it specifically for your system in fact.

---

### Post by dxlr8r on 2008-11-14
When will these mactel patches be standard in the Linux kernel? I use Arch Linux, and tried Ubuntu on my Mac Pro... And to be honest I miss Arch Linux :) Ubuntu is great, but I prefer pacman over aptitude.

---

### Post by kosumi68 on 2008-11-14
> **dxlr8r said:**
> When will these mactel patches be standard in the Linux kernel? I use Arch Linux, and tried Ubuntu on my Mac Pro... And to be honest I miss Arch Linux :) Ubuntu is great, but I prefer pacman over aptitude.

It will become standard as soon as somebody like yourself report results for the tests described in this thread. :-) I know you did try it once already, thanks, but did you notice the dkms package I attached soon after your report? If you could please go through the same procedure again, it should make a big difference. Thanks!

---

### Post by cyberdork33 on 2008-11-16
> **dxlr8r said:**
> When will these mactel patches be standard in the Linux kernel? I use Arch Linux, and tried Ubuntu on my Mac Pro... And to be honest I miss Arch Linux :) Ubuntu is great, but I prefer pacman over aptitude.

They are usually submitted upstream as soon as they are verified working properly. They then have to make it into your distro repos though.

---

### Post by hyperboloid on 2008-12-18
I hate to reopen this thread, but something appears to have gone wrong with applesmc, which I've been using happily for 6 weeks or so. But now I notice:
```

me@laptop:~$ dmesg | grep applesmc
[   15.985311] applesmc: Apple MacBook Pro 4 detected:
[   15.985315] applesmc:  - Model with accelerometer
[   15.985316] applesmc:  - Model with light sensors and backlight
[   15.985318] applesmc:  - Model with 12 temperature sensors
[   16.040746] applesmc: device successfully initialized (0xe0, 0x00).
[   16.040749] applesmc: device successfully initialized.
[   16.041703] applesmc: 2 fans found.
[   16.044824] input: applesmc as /devices/platform/applesmc.768/input/input12
[   16.072193] applesmc: driver successfully loaded.
[   78.238117] applesmc: light sensor data length set to 6
[ 1147.177492] applesmc: wait status failed: 4 != 5
[ 1148.582721] applesmc: wait status failed: 4 != 5
[ 1150.231960] applesmc: wait status failed: 4 != 5
[ 1156.748686] applesmc: wait status failed: 4 != 5
[ 1167.871484] applesmc: wait status failed: 4 != 5
[ 1742.456120] applesmc: wait status failed: 4 != 5
[ 2937.358790] applesmc: wait status failed: 5 != 1
[ 2940.498053] applesmc: wait status failed: 5 != 1
[ 2946.811860] applesmc: wait status failed: 4 != 0
[ 3068.287151] applesmc: wait status failed: 5 != 0
[ 3068.643088] applesmc: wait status failed: 5 != 0
[ 3069.096076] applesmc: wait status failed: 5 != 4
[ 3069.133776] applesmc: command failed: 12 -> e
[ 3069.270963] applesmc: wait status failed: 5 != 0
[ 3069.842272] applesmc: wait status failed: 5 != 0
[ 3070.389057] applesmc: wait status failed: 5 != 0
[ 3071.026342] applesmc: wait status failed: 5 != 0
[ 3071.081471] applesmc: wait status failed: 5 != 0
[ 3071.372196] applesmc: wait status failed: 5 != 0
[ 3071.435559] applesmc: wait status failed: 5 != 0
[ 3071.842024] applesmc: wait status failed: 5 != 0
[ 3071.936563] applesmc: wait status failed: 5 != 0
[ 3071.992569] applesmc: wait status failed: 5 != 0
[ 3072.071499] applesmc: wait status failed: 5 != 0
[ 3072.148329] applesmc: wait status failed: 5 != 0
[ 3072.655319] applesmc: wait status failed: 5 != 0
[ 3073.197051] applesmc: wait status failed: 5 != 0
[ 3073.540999] applesmc: wait status failed: 5 != 0
[ 3074.115340] applesmc: wait status failed: 5 != 0
[ 3074.219745] applesmc: wait status failed: 5 != 0
[ 3074.602889] applesmc: wait status failed: 5 != 0
[ 3074.648441] applesmc: wait status failed: 4 != 5
[ 3075.016513] applesmc: wait status failed: 5 != 0
[ 3075.159835] applesmc: wait status failed: 5 != 0
[ 3075.232513] applesmc: wait status failed: 5 != 0
[ 3075.558157] applesmc: wait status failed: 5 != 0
[ 3075.620663] applesmc: wait status failed: 5 != 0

```
Here is a very weird thing. The script "applesmc-test.sh" produced some errors when I first ran it, and then when I ran it again after some time had passed, it seemed to work again. Same with the script "scan-smc.sh" which gave an infinite loop of error messages (something about "0: #KEY [4-ui32]" over and over) at first, then ran OK later. I did nothing in between except browse the forums.

I'm attaching the outputs from these scripts after they started working.

---

### Post by cyberdork33 on 2008-12-19
Did an update appear in the Ubuntu repo? You might need to rebuild the mactel PPA package again if so to re-replace the update.

---

### Post by kosumi68 on 2010-03-14
> **hyperboloid said:**
> 
Here is a very weird thing. The script "applesmc-test.sh" produced some errors when I first ran it, and then when I ran it again after some time had passed, it seemed to work again. Same with the script "scan-smc.sh" which gave an infinite loop of error messages (something about "0: #KEY [4-ui32]" over and over) at first, then ran OK later. I did nothing in between except browse the forums.

I'm attaching the outputs from these scripts after they started working.

The reading of the SMC registers never was an exact science, and reading errors are still normal. By the look of it, you have a tiny but non-zero fail ratio on your machine, resulting in the test script sometimes reporting no errors, sometimes some errors. Nothing to worry about, as long as it seems to operate normally.

---

### Post by m.prebble on 2010-04-26
Hi guys,

I have a MBP 5,4, and have problems with the SMC not regulating the fan temperature. After digging through various forums, I have only found people having the same issue. For others, they have no problem. This is very frustrating, as I can't rely on thermal mgmt when using Linux - I am afraid to come back and find the a rogue app has cooked my CPU.

I have followed the steps in the top of this forum. Please find the output of this attached: 

```

0: #KEY [4-ui32] 00000134 [...4]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 07 [.]
4: ACCL [1-ui8 ]
5: ACEN [1-ui8 ] 01 [.]
6: ACFP [1-flag] 01 [.]
7: ACIC [2-ui16] 0e10 [..]
8: ACID [8-ch8*] 8598d028c00310e7 [...(....]
9: ACIN [1-flag] 01 [.]
10: ACLM [1-ui8 ] 55 [U]
11: AL! [2-ui16] 0000 [..]
12: ALA0 [6-{ala] ca1effd602d9 [......]
13: ALA1 [6-{ala] 30a4021f0315 [0.....]
14: ALA2 [6-{ala] 0cea02d40396 [......]
15: ALA3 [6-{ala] 0389036103dc [...a..]
16: ALA4 [6-{ala] 00ee03bc0400 [......]
17: ALA5 [6-{ala] 04fcfff30400 [......]
18: ALAT [4-{alt] 002b0308 [.+..]
19: ALI0 [4-{ali] 04000f00 [....]
20: ALI1 [4-{ali] 00000000 [....]
21: ALP0 [4-ui16] 13330780 [.3..]
22: ALP1 [4-ui16] 00000000 [....]
23: ALRV [2-ui16] 0001 [..]
24: ALSC [16-{alc] 00c8009603e8000f0001015e1d030106 [...........^....]
25: ALSF [2-fp1f] 4b44 [KD]
26: ALSL [2-ui16] 004d [.M]
27: ALT0 [2-ui16] 0000 [..]
28: ALT1 [2-ui16] 0000 [..]
29: ALTH [10-{alr] 00320070025200140041 [.2.p.R...A]
30: ALV0 [10-{alv] 010102ed01990013466a [........Fj]
31: ALV1 [10-{alv] 00010000000000000000 [..........]
32: AUPO [1-ui8 ] 00 [.]
33: B0AC [2-si16] 0000 [..]
34: B0AV [2-ui16] 3097 [0.]
35: B0Ad [2-ui16] 0000 [..]
36: B0Al [2-ui16] ffff [..]
37: B0Am [1-ui8 ] 10 [.]
38: B0Ar [1-ui8 ] 00 [.]
39: B0As [1-ui8 ] 00 [.]
40: B0At [2-ui16] 0960 [.`]
41: B0Au [2-ui16] 0960 [.`]
42: B0Az [1-ui8 ] 00 [.]
43: B0BI [1-ui8 ] 51 [Q]
44: B0CM [2-ui16] 0119 [..]
45: B0CT [2-ui16] 0060 [.`]
46: B0FC [2-ui16] 1958 [.X]
47: B0FV [2-ui16] 0003 [..]
48: B0LI [2-ui16] 7fff [..]
49: B0PS [2-ui16] 0000 [..]
50: B0RI [2-ui16] 0000 [..]
51: B0RM [2-ui16] 18e3 [..]
52: B0SN [13-ch8*] 57303932364245373737375641 [W0926BE7777VA]
53: B0St [2-ui16] 40e0 [@.]
54: B0TF [2-ui16] ffff [..]
55: BATP [1-flag] 00 [.]
56: BBAD [1-flag] 00 [.]
57: BBIN [1-flag] 01 [.]
58: BC1V [2-ui16] 1032 [.2]
59: BC2V [2-ui16] 1033 [.3]
60: BC3V [2-ui16] 1031 [.1]
61: BCHA [1-ui8 ] 02 [.]
62: BCHB [1-ui8 ] 06 [.]
63: BCHF [1-ui8 ]
64: BCHG [1-ui8 ]
65: BCHL [1-ui8 ]
66: BCHO [1-ui8 ] 1f [.]
67: BCHP [1-ui8 ] 13 [.]
68: BCHR [1-ui8 ] 3a [:]
69: BCHT [1-ui8 ] 06 [.]
70: BCHX [1-ui8 ] 01 [.]
71: BCLM [1-ui8 ] 64 [d]
72: BEZL [1-ui8 ] 00 [.]
73: BILB [1-ui8 ] 1f [.]
74: BILO [2-ui8 ] 1f12 [..]
75: BNCM [1-ui8 ]
76: BNCR [1-ui8 ] 04 [.]
77: BNum [1-ui8 ] 01 [.]
78: BRSC [2-ui16] 0063 [.c]
79: BSAC [1-ui8 ] 33 [3]
80: BSIn [1-ui8 ] 42 [B]
81: BTIL [2-ui16] 0780 [..]
82: BTTI [1-ui8 ] 02 [.]
83: BTVI [1-ui8 ] 03 [.]
84: BTVR [1-ui8 ] 01 [.]
85: BTVT [1-ui8 ] 01 [.]
86: CH2S [1-flag] 00 [.]
87: CHBI [2-ui16] 0000 [..]
88: CHBV [2-ui16] 3130 [10]
89: CHGC [2-ui16] 0040 [.@]
90: CHGD [1-flag]
91: CHGI [2-ui16] 0000 [..]
92: CHGV [2-ui16] 3130 [10]
93: CHPV [2-si16] 3130 [10]
94: CLK! [1-ui8 ]
95: CLKC [10-{clc] 00000e1000000e10198c [..........]
96: CLKH [8-{clh] 0000708000011940 [..p....@]
97: CLKS [2-fp1f] 198c [..]
98: CLKT [4-ui32] 000144d3 [..D.]
99: CLSD [2-ui16] 0000 [..]
100: CLWK [2-ui16] 0071 [.q]
101: CRCB [4-ui32] f0255a54 [.%ZT]
102: CRCU [4-ui32]
103: DPLM [3-{lim]
104: EPCA [4-ui32] 00007000 [..p.]
105: EPCF [1-flag] 01 [.]
106: EPCI [4-ui32] 03e00700 [....]
107: EPCV [2-ui16] 0001 [..]
108: EPMA [4-ch8*] 00006080 [..`.]
109: EPMI [1-ui8 ] 00 [.]
110: EPUA [4-ui32] 00006000 [..`.]
111: EPUF [1-flag] 01 [.]
112: EPUI [4-ui32] 03e00001 [....]
113: EPUV [2-ui16] 0001 [..]
114: EVCT [2-ui16] 4a0a [J.]
115: EVMD [4-ui32]
116: EVRD [32-ch8*] 730000046f013d33631a7281050092c536c4000003011fca62b736050100bf10 [s...o.=3c.r.....6.......b.6.....]
117: F0Ac [2-fpe2] 2eef [..]
118: F0ID [16-{fds] 00010c004c6566742073696465202000 [....Left side .]
119: F0Mn [2-fpe2] 2ee0 [..]
120: F0Mt [2-ui16] f400 [..]
121: F0Mx [2-fpe2] 5910 [Y.]
122: F0Tg [2-fpe2] 2ee0 [..]
123: FNum [1-ui8 ] 01 [.]
124: FPhz [2-si16]
125: FS! [2-ui16] 0000 [..]
126: HBWK [1-flag]
127: HDBS [1-ui8 ] 01 [.]
128: HDST [4-hex_] 00000000 [....]
129: HDSW [4-hex_] 0dcb0db0 [....]
130: IBIR [2-fp2e] 0000 [..]
131: IBIr [2-ui16] 0000 [..]
132: IC0C [2-fp6a] 0851 [.Q]
133: IC1C [2-fp4c] 047b [.{]
134: ID0R [2-fp3d] 2966 [)f]
135: ID0r [2-ui16] 2740 ['@]
136: ID1R [2-fp6a] 0000 [..]
137: ID1r [2-ui16] 0000 [..]
138: IH0C [2-fp4c] 0000 [..]
139: IH0r [2-ui16] 0000 [..]
140: IN0R [2-fp6a] 085c [.\]
141: IN1R [2-fp6a] 00e6 [..]
142: IO0C [2-fp4c] 0000 [..]
143: IO0r [2-ui16] 0000 [..]
144: IP0R [2-fp4c] 0241 [.A]
145: IP0r [2-ui16] 0380 [..]
146: IW0C [2-fp4c] 0000 [..]
147: IW0r [2-ui16] 0000 [..]
148: LAcN [1-ui8 ]
149: LAtN [2-ui16]
150: LCCN [1-ui8 ] e0 [.]
151: LCCQ [1-ui8 ] 0b [.]
152: LCKA [1-ui8 ] 6f [o]
153: LCSA [1-ui8 ] 28 [(]
154: LCTN [1-ui8 ] 59 [Y]
155: LCTQ [1-ui8 ] a0 [.]
156: LDSP [1-flag]
157: LKSB [2-{lkb]
158: LS! [1-ui8 ] 00 [.]
159: LSCF [10-{lsc] 00c80190800002020020 [......... ]
160: LSDD [8-{lsd] 0002000300030019 [........]
161: LSDU [8-{lsd] 0003000200140003 [........]
162: LSFD [6-{lsf] 00000004008c [......]
163: LSFU [6-{lsf] 00000004008c [......]
164: LSLB [2-{pwm] ffff [..]
165: LSLF [2-{pwm] 0000 [..]
166: LSLN [2-{pwm] ffff [..]
167: LSOF [1-flag] 01 [.]
168: LSOO [1-flag]
169: LSPV [2-{pwm] 0000 [..]
170: LSRB [1-flag]
171: LSSB [2-{lso]
172: LSSE [1-flag] 01 [.]
173: LSSS [2-{lso]
174: LSSV [2-ui16] ffff [..]
175: LSUP [1-ui8 ]
176: MACA [4-ui32] 00000000 [....]
177: MACM [1-flag] 01 [.]
178: MACR [32-ch8*]
179: MOCF [2-ui16] 8300 [..]
180: MOCN [2-ui16] e0f8 [..]
181: MOHD [1-ui8 ] 14 [.]
182: MOHT [2-sp78] 01c0 [..]
183: MOLD [1-ui8 ] 14 [.]
184: MOLT [2-sp78] 0060 [.`]
185: MOST [2-ui16] 8003 [..]
186: MOVX [2-sp78] 0016 [..]
187: MOVY [2-sp78] ffea [..]
188: MOVZ [2-sp78] 0102 [..]
189: MO_X [2-sp78] 0016 [..]
190: MO_Y [2-sp78] ffea [..]
191: MO_Z [2-sp78] 0101 [..]
192: MSAL [1-ui8 ] 4b [K]
193: MSAR [2-ui16] 0000 [..]
194: MSAc [2-fp88] 0000 [..]
195: MSAg [2-fp88] 0000 [..]
196: MSAm [2-fp88] 0000 [..]
197: MSBC [2-ui16] 0000 [..]
198: MSBP [2-ui16] 1191 [..]
199: MSBc [2-ui16] 0000 [..]
200: MSBp [2-ui16] 1191 [..]
201: MSDI [1-flag] 00 [.]
202: MSDW [1-flag]
203: MSFG [1-ui8 ] 00 [.]
204: MSLD [1-ui8 ] 00 [.]
205: MSPA [2-fp6a] 0000 [..]
206: MSPC [1-ui8 ] 06 [.]
207: MSPS [2-ui16] 0001 [..]
208: MSPZ [1-ui8 ] 08 [.]
209: MSPs [2-ui16] 0000 [..]
210: MSSD [1-si8 ] 05 [.]
211: MSSE [2-ui16] 0000 [..]
212: MSSF [4-ui32] 00000001 [....]
213: MSSP [1-si8 ] 05 [.]
214: MSSS [1-{mss] 00 [.]
215: MSTC [2-ui16] 0000 [..]
216: MSTM [1-ui8 ] 01 [.]
217: MSTc [1-ui8 ] 00 [.]
218: MSTg [1-ui8 ] 00 [.]
219: MSTm [1-ui8 ] 00 [.]
220: MSWR [1-ui8 ]
221: MSXC [4-ch8*] 00000000 [....]
222: MSXD [16-ch8*] 00000000000000000000000000000000 [................]
223: MSXK [32-ch8*] 0102030405060708090a0b0c0d0e0f1011120000000000000000000000000000 [................................]
224: MSXN [1-ui8 ] 12 [.]
225: MSXS [4-ch8*] 0205070a [....]
226: MSXb [1-ui8 ] 00 [.]
227: MSXc [4-ch8*] 00000000 [....]
228: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
229: MSXk [32-ch8*] 0102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f20 [............................... ]
230: MSXm [2-ui16] 0008 [..]
231: MSXn [1-ui8 ] 28 [(]
232: MSXs [4-ui32] 0103060c [....]
233: NACK [1-flag]
234: NATJ [1-ui8 ] 00 [.]
235: NATi [2-ui16] 0000 [..]
236: NOPB [1-ui8 ] 00 [.]
237: NTOK [1-ui8 ]
238: ONMI [1-ui8 ] 00 [.]
239: OWCT [2-ui16] 000e [..]
240: PBIC [2-fp88] 0000 [..]
241: PC0C [2-fp88] 03cd [..]
242: PC1C [2-fp88] 05bb [..]
243: PD0R [2-fp88] 17d3 [..]
244: PD1R [2-fp88] 0000 [..]
245: PH0C [2-fp88] 0000 [..]
246: PHPC [2-fp88] 0845 [.E]
247: PN0R [2-fp88] 0234 [.4]
248: PN1R [2-fp88] 0056 [.V]
249: PO0C [2-fp88] 0000 [..]
250: PP0R [2-fp88] 01c4 [..]
251: PTHC [2-fp88] 20fb [ .]
252: PW0C [2-fp88] 0000 [..]
253: RBr [8-ch8*] 6b31396900000000 [k19i....]
254: REV [6-{rev] 01490f000002 [.I....]
255: RMde [1-char] 41 [A]
256: RPlt [8-ch8*] 6b31396900000000 [k19i....]
257: RSvn [4-ui32] 00006446 [..dF]
258: RVBF [6-{rev] 01490f000002 [.I....]
259: RVUF [6-{rev] 01490f000002 [.I....]
260: SAS! [4-hex_]
261: SBS! [2-ui16]
262: SCIA [2-ui16] 03f8 [..]
263: SCIL [1-ui8] 00 [.]
264: SDRd [2-ui16]
265: SIP [1-ui8] 01 [.]
266: SIS! [2-hex_]
267: SIT! [2-hex_]
268: SM0x [2-ui16] 7c40 [|@]
269: SM0y [2-ui16] 8340 [.@]
270: SM0z [2-ui16] b3c0 [..]
271: SMBC [5-ch8*]
272: SMBG [1-ui8 ]
273: SMBR [32-ch8*]
274: SMBS [2-ch8*]
275: SMBW [32-ch8*]
276: SPH0 [2-ui16] 2992 [).]
277: SPHS [1-ui8 ] 00 [.]
278: SPHT [1-ui8 ] 00 [.]
279: SPHZ [1-ui8]
280: SPS! [2-ui16]
281: TB0T [2-sp78] 1e4c [.L]
282: TB1T [2-sp78] 1e4c [.L]
283: TB2T [2-sp78] 1d00 [..]
284: TB3T [2-sp78] 0000 [..]
285: TC0D [2-sp78] 3760 [7`]
286: TC0F [2-sp78] 2f56 [/V]
287: TC0P [2-sp78] 3100 [1.]
288: TN0D [2-sp78] 3620 [6 ]
289: TN0P [2-sp78] 2ea0 [..]
290: TTF0 [2-sp78] 3100 [1.]
291: Th2H [2-sp78] 2dc0 [-.]
292: Ts0P [2-sp78] 1c40 [.@]
293: Ts0S [2-sp78] 2444 [$D]
294: UPRC [2-ui16] 0845 [.E]
295: VBOC [2-fp6a] 0000 [..]
296: VBOc [2-ui16] 0000 [..]
297: VC0C [2-fp2e] 43bc [C.]
298: VC0c [2-ui16] 5a40 [Z@]
299: VN0R [2-fp2e] 3fff [?.]

```Can anyone possibly shed some light on this for me? fan1_manual is 0.  Kind regards,

Here is my dmsg output:
```


(Many more before this)
[ 2866.895374] applesmc: wait status failed: 5 != 0
[ 2866.928232] applesmc: wait status failed: 5 != 0
[ 2866.961124] applesmc: wait status failed: 5 != 0
[ 2866.997974] applesmc: wait status failed: 5 != 0
[ 2867.040855] applesmc: wait status failed: 5 != 0
[ 2867.073667] applesmc: wait status failed: 5 != 0
[ 2867.109340] applesmc: wait status failed: 5 != 0
[ 2867.143917] applesmc: wait status failed: 5 != 0
[ 2867.176778] applesmc: wait status failed: 5 != 0
[ 2867.209802] applesmc: wait status failed: 5 != 0
[ 2867.246832] applesmc: wait status failed: 5 != 0
[ 2867.288783] applesmc: wait status failed: 5 != 0
[ 2867.321608] applesmc: wait status failed: 5 != 0
[ 2867.357032] applesmc: wait status failed: 5 != 0
[ 2867.390128] applesmc: wait status failed: 5 != 0
[ 2867.422935] applesmc: wait status failed: 5 != 0
[ 2867.455741] applesmc: wait status failed: 5 != 0
[ 2867.497112] applesmc: wait status failed: 5 != 0
[ 2867.538676] applesmc: wait status failed: 5 != 0
[ 2867.571490] applesmc: wait status failed: 5 != 0
[ 2867.607085] applesmc: wait status failed: 5 != 0
[ 2867.639999] applesmc: wait status failed: 5 != 0
[ 2867.672884] applesmc: wait status failed: 5 != 0
[ 2867.706434] applesmc: wait status failed: 5 != 0
[ 2867.743508] applesmc: wait status failed: 5 != 0
[ 2867.785468] applesmc: wait status failed: 5 != 0
[ 2867.818277] applesmc: wait status failed: 5 != 0
[ 2867.855732] applesmc: wait status failed: 5 != 0
[ 2867.893148] applesmc: wait status failed: 5 != 0
[ 2867.925998] applesmc: wait status failed: 5 != 0
[ 2867.958804] applesmc: wait status failed: 5 != 0
[ 2867.995312] applesmc: wait status failed: 5 != 0
[ 2868.037271] applesmc: wait status failed: 5 != 0
[ 2868.070078] applesmc: wait status failed: 5 != 0
[ 2868.105554] applesmc: wait status failed: 5 != 0
[ 2868.139460] applesmc: wait status failed: 5 != 0
[ 2868.172276] applesmc: wait status failed: 5 != 0
[ 2868.205087] applesmc: wait status failed: 5 != 0
[ 2868.242107] applesmc: wait status failed: 5 != 0
[ 2868.286271] applesmc: wait status failed: 5 != 0
[ 2868.319083] applesmc: wait status failed: 5 != 0
[ 2868.354592] applesmc: wait status failed: 5 != 0
[ 2868.387518] applesmc: wait status failed: 5 != 0
[ 2868.420333] applesmc: wait status failed: 5 != 0
[ 2868.453144] applesmc: wait status failed: 5 != 0
[ 2868.491307] applesmc: wait status failed: 5 != 0
[ 2868.532904] applesmc: wait status failed: 5 != 0
[ 2868.565717] applesmc: wait status failed: 5 != 0
[ 2868.601705] applesmc: wait status failed: 5 != 0
[ 2868.635068] applesmc: wait status failed: 5 != 0
[ 2868.668262] applesmc: wait status failed: 5 != 0
[ 2868.701093] applesmc: wait status failed: 5 != 0
[ 2868.738888] applesmc: wait status failed: 5 != 0
[ 2868.782822] applesmc: wait status failed: 5 != 0
[ 2868.815631] applesmc: wait status failed: 5 != 0
[ 2868.853941] applesmc: wait status failed: 5 != 0
[ 2868.887535] applesmc: wait status failed: 5 != 0
[ 2868.920346] applesmc: wait status failed: 5 != 0
[ 2868.953156] applesmc: wait status failed: 5 != 0
[ 2868.989667] applesmc: wait status failed: 5 != 0
[ 2869.031752] applesmc: wait status failed: 5 != 0
[ 2869.064560] applesmc: wait status failed: 5 != 0
[ 3044.253372] applesmc: wait status failed: 5 != 0
[ 3046.171132] applesmc: wait status failed: 5 != 0
[ 3046.226736] applesmc: wait status failed: 5 != 0
[ 3046.282905] applesmc: wait status failed: 5 != 0
[ 3046.563544] applesmc: wait status failed: 5 != 0
[ 3046.772481] applesmc: wait status failed: 4 != 5
[ 3047.179824] applesmc: wait status failed: 5 != 0
[ 3047.364443] applesmc: wait status failed: 4 != 5
[ 3047.576426] applesmc: wait status failed: 4 != 5
[ 3047.789169] applesmc: wait status failed: 5 != 4
[ 3047.824862] applesmc: command failed: 12 -> e
[ 3047.872516] applesmc: command failed: 10 -> 8
[ 3047.945687] applesmc: wait status failed: 5 != 0
[ 3048.444321] applesmc: wait status failed: 5 != 0
[ 3048.845766] applesmc: wait status failed: 5 != 0
[ 3048.928590] applesmc: wait status failed: 4 != 5
[ 3049.770745] applesmc: wait status failed: 5 != 0
[ 3049.839235] applesmc: wait status failed: 5 != 0
[ 3050.130181] applesmc: wait status failed: 5 != 0
[ 3050.200773] applesmc: wait status failed: 5 != 0
[ 3050.665543] applesmc: wait status failed: 5 != 0
[ 3050.728575] applesmc: wait status failed: 4 != 5
[ 3050.851919] applesmc: wait status failed: 5 != 0
[ 3050.922045] applesmc: wait status failed: 5 != 0
[ 3051.036258] applesmc: wait status failed: 5 != 0
[ 3051.150109] applesmc: wait status failed: 5 != 0
[ 3051.254577] applesmc: wait status failed: 5 != 0
[ 3052.037991] applesmc: wait status failed: 5 != 0
[ 3052.648339] applesmc: wait status failed: 5 != 0
[ 3053.045371] applesmc: wait status failed: 5 != 0
[ 3053.177547] applesmc: wait status failed: 5 != 0
[ 3053.831860] applesmc: wait status failed: 5 != 0
[ 3053.893642] applesmc: wait status failed: 5 != 0
[ 3053.995580] applesmc: wait status failed: 5 != 0
[ 3054.075667] applesmc: wait status failed: 5 != 0
[ 3054.158045] applesmc: wait status failed: 5 != 0
[ 3054.288659] applesmc: wait status failed: 5 != 0
[ 3054.347425] applesmc: wait status failed: 5 != 0
[ 3054.418522] applesmc: wait status failed: 5 != 0
[ 3054.489607] applesmc: wait status failed: 5 != 0
[ 3054.565982] applesmc: wait status failed: 5 != 0
[ 3054.696608] applesmc: wait status failed: 5 != 0
[ 3054.755403] applesmc: wait status failed: 5 != 0


```

Marcus

---

### Post by kosumi68 on 2010-04-26
Thanks for providing the data. Please find attached a package for testing the MBP5,4 settings. I have to ask again if this is indeed a MacBook Pro? Is so, the 5,4 model has only one fan, which might explain one or two things.

Output of the test scripts after unpacking and installing this package followed by a reboot would be greatly appreciated.

Cheers!

---

### Post by m.prebble on 2010-04-26
Hi, 

Thank you very much for taking the time to investigate this with me. Yep, definitely macbook pro, 5.4 model according to dmidecode.

Installed the package, here is the output. Unfortunately the fan still stayed static at 2000rpm throughout the testing.


```

accelerometer: present, readable, output: (7,43,253)
fan:           present, readable, output: 2000
light:         present, readable, output: (2,0)
leds:          present,
 led:                   readable, output: 100
temperatures:  present,
 temperature:           readable, output: 49000
 temperature:           readable, output: 40750
 temperature:           readable, output: 26250
 temperature:           readable, output: 34500
 temperature:           readable, output: 27250
 temperature:           readable, output: 27250
 temperature:           readable, output: 27000
 temperature:           readable, output: 0
 temperature:           readable, output: 49250
 temperature:           readable, output: 43250
 temperature:           readable, output: 45250
 temperature:           readable, output: 50000
 temperature:           readable, output: 43500
performance:   reading all temperatures
 fail frequency:        .002
 reads per second:      62

```

```

0: #KEY [4-ui32] 00000134 [...4]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 07 [.]
4: ACCL [1-ui8 ]
5: ACEN [1-ui8 ] 01 [.]
6: ACFP [1-flag] 01 [.]
7: ACIC [2-ui16] 0e10 [..]
8: ACID [8-ch8*] 8598d028c00310e7 [...(....]
9: ACIN [1-flag] 01 [.]
10: ACLM [1-ui8 ] 55 [U]
11: AL! [2-ui16] 0000 [..]
12: ALA0 [6-{ala] ca1effd602d9 [......]
13: ALA1 [6-{ala] 30a4021f0315 [0.....]
14: ALA2 [6-{ala] 0cea02d40396 [......]
15: ALA3 [6-{ala] 0389036103dc [...a..]
16: ALA4 [6-{ala] 00ee03bc0400 [......]
17: ALA5 [6-{ala] 04fcfff30400 [......]
18: ALAT [4-{alt] 002b0308 [.+..]
19: ALI0 [4-{ali] 04000f00 [....]
20: ALI1 [4-{ali] 00000000 [....]
21: ALP0 [4-ui16] 13330780 [.3..]
22: ALP1 [4-ui16] 00000000 [....]
23: ALRV [2-ui16] 0001 [..]
24: ALSC [16-{alc] 00c8009603e8000f0001015e1d030106 [...........^....]
25: ALSF [2-fp1f] 3873 [8s]
26: ALSL [2-ui16] 0030 [.0]
27: ALT0 [2-ui16] 0000 [..]
28: ALT1 [2-ui16] 0000 [..]
29: ALTH [10-{alr] 00320070025200140041 [.2.p.R...A]
30: ALV0 [10-{alv] 010101cd00fa000c1296 [..........]
31: ALV1 [10-{alv] 00010000000000000000 [..........]
32: AUPO [1-ui8 ] 00 [.]
33: B0AC [2-si16] 0000 [..]
34: B0AV [2-ui16] 3091 [0.]
35: B0Ad [2-ui16] 0000 [..]
36: B0Al [2-ui16] ffff [..]
37: B0Am [1-ui8 ] 10 [.]
38: B0Ar [1-ui8 ] 00 [.]
39: B0As [1-ui8 ] 00 [.]
40: B0At [2-ui16] 0960 [.`]
41: B0Au [2-ui16] 0960 [.`]
42: B0Az [1-ui8 ] 00 [.]
43: B0BI [1-ui8 ] 51 [Q]
44: B0CM [2-ui16] 0119 [..]
45: B0CT [2-ui16] 0060 [.`]
46: B0FC [2-ui16]
47: B0FV [2-ui16] 0003 [..]
48: B0LI [2-ui16] 7fff [..]
49: B0PS [2-ui16] 0000 [..]
50: B0RI [2-ui16] 0000 [..]
51: B0RM [2-ui16] 1936 [.6]
52: B0SN [13-ch8*] 57303932364245373737375641 [W0926BE7777VA]
53: B0St [2-ui16] 40e0 [@.]
54: B0TF [2-ui16] ffff [..]
55: BATP [1-flag] 00 [.]
56: BBAD [1-flag] 00 [.]
57: BBIN [1-flag] 01 [.]
58: BC1V [2-ui16] 1030 [.0]
59: BC2V [2-ui16] 1031 [.1]
60: BC3V [2-ui16] 1030 [.0]
61: BCHA [1-ui8 ] 02 [.]
62: BCHB [1-ui8 ] 01 [.]
63: BCHF [1-ui8 ]
64: BCHG [1-ui8 ]
65: BCHL [1-ui8 ]
66: BCHO [1-ui8 ] 1f [.]
67: BCHP [1-ui8 ] 01 [.]
68: BCHR [1-ui8 ] 3a [:]
69: BCHT [1-ui8 ] 06 [.]
70: BCHX [1-ui8 ] 01 [.]
71: BCLM [1-ui8 ] 64 [d]
72: BEZL [1-ui8 ] 00 [.]
73: BILB [1-ui8 ] 1f [.]
74: BILO [2-ui8 ] 1f0e [..]
75: BNCM [1-ui8 ]
76: BNCR [1-ui8 ] 04 [.]
77: BNum [1-ui8 ] 01 [.]
78: BRSC [2-ui16] 0062 [.b]
79: BSAC [1-ui8 ] 33 [3]
80: BSIn [1-ui8 ] 42 [B]
81: BTIL [2-ui16] 0780 [..]
82: BTTI [1-ui8 ] 02 [.]
83: BTVI [1-ui8 ] 03 [.]
84: BTVR [1-ui8 ] 01 [.]
85: BTVT [1-ui8 ] 01 [.]
86: CH2S [1-flag] 00 [.]
87: CHBI [2-ui16] 0000 [..]
88: CHBV [2-ui16] 3138 [18]
89: CHGC [2-ui16] 0040 [.@]
90: CHGD [1-flag]
91: CHGI [2-ui16] 0000 [..]
92: CHGV [2-ui16] 3130 [10]
93: CHPV [2-si16] 3130 [10]
94: CLK! [1-ui8 ] 00 [.]
95: CLKC [10-{clc] 00000e1000000e10198c [..........]
96: CLKH [8-{clh] 0000708000011940 [..p....@]
97: CLKS [2-fp1f] 8000 [..]
98: CLKT [4-ui32] 0000e03b [...;]
99: CLSD [2-ui16] 0000 [..]
100: CLWK [2-ui16] 0076 [.v]
101: CRCB [4-ui32] f0255a54 [.%ZT]
102: CRCU [4-ui32]
103: DPLM [3-{lim]
104: EPCA [4-ui32] 00007000 [..p.]
105: EPCF [1-flag] 01 [.]
106: EPCI [4-ui32] 03e00700 [....]
107: EPCV [2-ui16] 0001 [..]
108: EPMA [4-ch8*] 00006080 [..`.]
109: EPMI [1-ui8 ] 00 [.]
110: EPUA [4-ui32] 00006000 [..`.]
111: EPUF [1-flag] 01 [.]
112: EPUI [4-ui32] 03e00001 [....]
113: EPUV [2-ui16] 0001 [..]
114: EVCT [2-ui16] 0505 [..]
115: EVMD [4-ui32]
116: EVRD [32-ch8*] 2303fa0001014a8d2304fa0001014a8df60601000000d83c760600000200858e [#.....J.#.....J........<v.......]
117: F0Ac [2-fpe2] 1f19 [..]
118: F0ID [16-{fds] 00010c004c6566742073696465202000 [....Left side .]
119: F0Mn [2-fpe2] 1f40 [.@]
120: F0Mt [2-ui16] f400 [..]
121: F0Mx [2-fpe2] 5910 [Y.]
122: F0Tg [2-fpe2] 1f40 [.@]
123: FNum [1-ui8 ] 01 [.]
124: FPhz [2-si16]
125: FS! [2-ui16] 0000 [..]
126: HBWK [1-flag] 00 [.]
127: HDBS [1-ui8 ] 00 [.]
128: HDST [4-hex_] 00000000 [....]
129: HDSW [4-hex_] 0dcd0db2 [....]
130: IBIR [2-fp2e] 0000 [..]
131: IBIr [2-ui16] 0000 [..]
132: IC0C [2-fp6a] 0dcd [..]
133: IC1C [2-fp4c] 06f1 [..]
134: ID0R [2-fp3d] 2e5d [.]]
135: ID0r [2-ui16] 2b80 [+.]
136: ID1R [2-fp6a] 0000 [..]
137: ID1r [2-ui16] 0000 [..]
138: IH0C [2-fp4c] 0000 [..]
139: IH0r [2-ui16] 0000 [..]
140: IN0R [2-fp6a] 087b [.{]
141: IN1R [2-fp6a] 00e9 [..]
142: IO0C [2-fp4c] 0000 [..]
143: IO0r [2-ui16] 0000 [..]
144: IP0R [2-fp4c] 0241 [.A]
145: IP0r [2-ui16] 0380 [..]
146: IW0C [2-fp4c] 0000 [..]
147: IW0r [2-ui16] 0000 [..]
148: LAcN [1-ui8 ]
149: LAtN [2-ui16]
150: LCCN [1-ui8 ] a5 [.]
151: LCCQ [1-ui8 ] 84 [.]
152: LCKA [1-ui8 ] 68 [h]
153: LCSA [1-ui8 ] 76 [v]
154: LCTN [1-ui8 ] 7b [{]
155: LCTQ [1-ui8 ] de [.]
156: LDSP [1-flag]
157: LKSB [2-{lkb]
158: LS! [1-ui8 ] 00 [.]
159: LSCF [10-{lsc] 00c80190800002020020 [......... ]
160: LSDD [8-{lsd] 0002000300030019 [........]
161: LSDU [8-{lsd] 0003000200140003 [........]
162: LSFD [6-{lsf] 00000004008c [......]
163: LSFU [6-{lsf] 00000004008c [......]
164: LSLB [2-{pwm] ffff [..]
165: LSLF [2-{pwm] 0000 [..]
166: LSLN [2-{pwm] ffff [..]
167: LSOF [1-flag] 01 [.]
168: LSOO [1-flag]
169: LSPV [2-{pwm] 0000 [..]
170: LSRB [1-flag]
171: LSSB [2-{lso]
172: LSSE [1-flag] 01 [.]
173: LSSS [2-{lso]
174: LSSV [2-ui16] ffff [..]
175: LSUP [1-ui8 ]
176: MACA [4-ui32] 00000000 [....]
177: MACM [1-flag] 01 [.]
178: MACR [32-ch8*]
179: MOCF [2-ui16] 8300 [..]
180: MOCN [2-ui16] e0f8 [..]
181: MOHD [1-ui8 ] 14 [.]
182: MOHT [2-sp78] 01c0 [..]
183: MOLD [1-ui8 ] 14 [.]
184: MOLT [2-sp78] 0060 [.`]
185: MOST [2-ui16] 8003 [..]
186: MOVX [2-sp78] 0005 [..]
187: MOVY [2-sp78] 002b [.+]
188: MOVZ [2-sp78] 0100 [..]
189: MO_X [2-sp78] 0002 [..]
190: MO_Y [2-sp78] 002c [.,]
191: MO_Z [2-sp78] 0100 [..]
192: MSAL [1-ui8 ] 4b [K]
193: MSAR [2-ui16] 0000 [..]
194: MSAc [2-fp88] 0000 [..]
195: MSAg [2-fp88] 0000 [..]
196: MSAm [2-fp88] 0000 [..]
197: MSBC [2-ui16] 0000 [..]
198: MSBP [2-ui16] 0fe4 [..]
199: MSBc [2-ui16] 0000 [..]
200: MSBp [2-ui16] 0fe4 [..]
201: MSDI [1-flag] 00 [.]
202: MSDW [1-flag]
203: MSFG [1-ui8 ] 00 [.]
204: MSLD [1-ui8 ] 00 [.]
205: MSPA [2-fp6a] 0000 [..]
206: MSPC [1-ui8 ] 06 [.]
207: MSPS [2-ui16] 0001 [..]
208: MSPZ [1-ui8 ] 08 [.]
209: MSPs [2-ui16] 0000 [..]
210: MSSD [1-si8 ] 03 [.]
211: MSSE [2-ui16] 0000 [..]
212: MSSF [4-ui32] 00000001 [....]
213: MSSP [1-si8 ] 05 [.]
214: MSSS [1-{mss] 00 [.]
215: MSTC [2-ui16] 0000 [..]
216: MSTM [1-ui8 ] 01 [.]
217: MSTc [1-ui8 ] 00 [.]
218: MSTg [1-ui8 ] 00 [.]
219: MSTm [1-ui8 ] 00 [.]
220: MSWR [1-ui8 ]
221: MSXC [4-ch8*] 00000000 [....]
222: MSXD [16-ch8*] 00000000000000000000000000000000 [................]
223: MSXK [32-ch8*] 0102030405060708090a0b0c0d0e0f1011120000000000000000000000000000 [................................]
224: MSXN [1-ui8 ] 12 [.]
225: MSXS [4-ch8*] 0205070a [....]
226: MSXb [1-ui8 ] 00 [.]
227: MSXc [4-ch8*] 00000000 [....]
228: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
229: MSXk [32-ch8*] 0102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f20 [............................... ]
230: MSXm [2-ui16] 0008 [..]
231: MSXn [1-ui8 ] 28 [(]
232: MSXs [4-ui32] 0103060c [....]
233: NACK [1-flag]
234: NATJ [1-ui8 ] 00 [.]
235: NATi [2-ui16] 0000 [..]
236: NOPB [1-ui8 ] 00 [.]
237: NTOK [1-ui8 ]
238: ONMI [1-ui8 ] 00 [.]
239: OWCT [2-ui16] 0010 [..]
240: PBIC [2-fp88] 0000 [..]
241: PC0C [2-fp88] 0211 [..]
242: PC1C [2-fp88] 0398 [..]
243: PD0R [2-fp88] 15ce [..]
244: PD1R [2-fp88] 0000 [..]
245: PH0C [2-fp88] 0000 [..]
246: PHPC [2-fp88]
247: PN0R [2-fp88] 021d [..]
248: PN1R [2-fp88] 0057 [.W]
249: PO0C [2-fp88] 0000 [..]
250: PP0R [2-fp88] 01c4 [..]
251: PTHC [2-fp88] 20fb [ .]
252: PW0C [2-fp88] 0000 [..]
253: RBr [8-ch8*] 6b31396900000000 [k19i....]
254: REV [6-{rev] 01490f000002 [.I....]
255: RMde [1-char] 41 [A]
256: RPlt [8-ch8*] 6b31396900000000 [k19i....]
257: RSvn [4-ui32] 00006446 [..dF]
258: RVBF [6-{rev] 01490f000002 [.I....]
259: RVUF [6-{rev] 01490f000002 [.I....]
260: SAS! [4-hex_]
261: SBS! [2-ui16]
262: SCIA [2-ui16] 03f8 [..]
263: SCIL [1-ui8] 00 [.]
264: SDRd [2-ui16]
265: SIP [1-ui8] 01 [.]
266: SIS! [2-hex_]
267: SIT! [2-hex_]
268: SM0x [2-ui16] 8000 [..]
269: SM0y [2-ui16] 7680 [v.]
270: SM0z [2-ui16] b2c0 [..]
271: SMBC [5-ch8*]
272: SMBG [1-ui8 ]
273: SMBR [32-ch8*]
274: SMBS [2-ch8*]
275: SMBW [32-ch8*]
276: SPH0 [2-ui16] 2a60 [*`]
277: SPHS [1-ui8 ] 00 [.]
278: SPHT [1-ui8 ] 00 [.]
279: SPHZ [1-ui8]
280: SPS! [2-ui16]
281: TB0T [2-sp78] 1b99 [..]
282: TB1T [2-sp78] 1b99 [..]
283: TB2T [2-sp78] 1b4c [.L]
284: TB3T [2-sp78] 0000 [..]
285: TC0D [2-sp78] 3740 [7@]
286: TC0F [2-sp78] 2b97 [+.]
287: TC0P [2-sp78] 2de0 [-.]
288: TN0D [2-sp78] 3320 [3 ]
289: TN0P [2-sp78] 2ba0 [+.]
290: TTF0 [2-sp78] 3100 [1.]
291: Th2H [2-sp78] 29a0 [).]
292: Ts0P [2-sp78] 1ac0 [..]
293: Ts0S [2-sp78] 22cd [".]
294: UPRC [2-ui16] 0845 [.E]
295: VBOC [2-fp6a] 0000 [..]
296: VBOc [2-ui16] 0000 [..]
297: VC0C [2-fp2e] 450e [E.]
298: VC0c [2-ui16] 4d40 [M@]
299: VN0R [2-fp2e] 3fff [?.]

```

I am happy to try anything more to get this solved. 

Kind regards,

Marcus

---

### Post by kosumi68 on 2010-04-26
Thanks, I take it there are fewer errors in dmesg? If so, it is a valid kernel patch, although for a different problem. If you want your name to appear as a tester in the kernel logs, please send me a private message with your full name and email address, and I will include it in the patch.

Just to get a clean baseline, did you try to set the /sys/devices/platform/applesmc.768/fan1_manual to one, then to zero again, after applying the package? Just to rule out that stopping reading of non-existing temperature sensors did not somehow magically solve the problem. I would also consider resetting the SMC (support.apple.com/kb/HT3964?viewlocale=en_US).

---

### Post by kosumi68 on 2010-04-26
Looking at the data again I realize Apple added even more sensors to the new machines, so the scan-smc.sh script needs to be changed slightly. Modify the line starting with "END=" to
```

END=400

```
and run the script again - you should see more entrys after the last one (299: VN0R).

---

### Post by kosumi68 on 2010-04-26
Looking even more at the data and comparing to other models, it seems one fan register (F0Sf) has been dropped for the new models MB51, MBA21, MBP51, MBP54. That register is commonly referred to as "safe speed".

Because the register has been removed, it is likely that Apple changed the way fan control works. It could well be that the SMC overheat protection that keeps the other models cool enough under Linux was removed and replaced by something else. Anyone's guess at this point.

In practise, it means the fan might have to be regulated by the OS for all those newer models. Are there any new mac owners out there that beg to differ?

---

### Post by m.prebble on 2010-04-26
Kosumi68, thank you again for your continued efforts on this. In reply to your previous message re: dmsg output, no, this is not the case... and now intermittently i get errors reading from TG0T GPU transistor..

But the number has changed again now: 
```
 

marcus@marcus-ubuntu:~/scripts$ dmesg | tail
[ 7340.889817] applesmc: wait status failed: 4 != 0
[ 7648.893822] applesmc: wait status failed: 4 != 0
[ 9082.888785] applesmc: wait status failed: 5 != 1
[ 9452.889228] applesmc: wait status failed: 4 != 0
[ 9518.894479] applesmc: wait status failed: 4 != 0
[10050.887675] applesmc: wait status failed: 4 != 0
[10092.895570] applesmc: wait status failed: 5 != 1
[10114.896571] applesmc: wait status failed: 5 != 1
[10292.890494] applesmc: wait status failed: 4 != 0
[10344.887784] applesmc: wait status failed: 5 != 1


```

```

here is the updated script output:

0: #KEY [4-ui32] 00000134 [...4]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 07 [.]
4: ACCL [1-ui8 ]
5: ACEN [1-ui8 ] 00 [.]
6: ACFP [1-flag] 00 [.]
7: ACIC [2-ui16] 0000 [..]
8: ACID [8-ch8*] 0000000000000000 [........]
9: ACIN [1-flag] 00 [.]
10: ACLM [1-ui8 ] 55 [U]
11: AL! [2-ui16] 0000 [..]
12: ALA0 [6-{ala] ca1effd602d9 [......]
13: ALA1 [6-{ala] 30a4021f0315 [0.....]
14: ALA2 [6-{ala] 0cea02d40396 [......]
15: ALA3 [6-{ala] 0389036103dc [...a..]
16: ALA4 [6-{ala] 00ee03bc0400 [......]
17: ALA5 [6-{ala] 04fcfff30400 [......]
18: ALAT [4-{alt] 002b0308 [.+..]
19: ALI0 [4-{ali] 04000f00 [....]
20: ALI1 [4-{ali] 00000000 [....]
21: ALP0 [4-ui16] 13330780 [.3..]
22: ALP1 [4-ui16] 00000000 [....]
23: ALRV [2-ui16] 0001 [..]
24: ALSC [16-{alc] 00c8009603e8000f0001015e1d030106 [...........^....]
25: ALSF [2-fp1f] 4b44 [KD]
26: ALSL [2-ui16] 004d [.M]
27: ALT0 [2-ui16] 0000 [..]
28: ALT1 [2-ui16] 0000 [..]
29: ALTH [10-{alr] 00320070025200140041 [.2.p.R...A]
30: ALV0 [10-{alv] 01010228010b00135312 [...(....S.]
31: ALV1 [10-{alv] 00010000000000000000 [..........]
32: AUPO [1-ui8 ] 00 [.]
33: B0AC [2-si16] fa1a [..]
34: B0AV [2-ui16] 2f62 [/b]
35: B0Ad [2-ui16] 0000 [..]
36: B0Al [2-ui16] ffff [..]
37: B0Am [1-ui8 ] 10 [.]
38: B0Ar [1-ui8 ] 00 [.]
39: B0As [1-ui8 ] 00 [.]
40: B0At [2-ui16] 0960 [.`]
41: B0Au [2-ui16] 0960 [.`]
42: B0Az [1-ui8 ] 00 [.]
43: B0BI [1-ui8 ] 51 [Q]
44: B0CM [2-ui16] 0119 [..]
45: B0CT [2-ui16] 0060 [.`]
46: B0FC [2-ui16] 19b1 [..]
47: B0FV [2-ui16] 0003 [..]
48: B0LI [2-ui16] 7fff [..]
49: B0PS [2-ui16] 0000 [..]
50: B0RI [2-ui16] 0000 [..]
51: B0RM [2-ui16] 1869 [.i]
52: B0SN [13-ch8*] 57303932364245373737375641 [W0926BE7777VA]
53: B0St [2-ui16] 40e0 [@.]
54: B0TF [2-ui16] ffff [..]
55: BATP [1-flag] 01 [.]
56: BBAD [1-flag] 00 [.]
57: BBIN [1-flag] 01 [.]
58: BC1V [2-ui16] 0fca [..]
59: BC2V [2-ui16] 0fcf [..]
60: BC3V [2-ui16] 0fca [..]
61: BCHA [1-ui8 ] 02 [.]
62: BCHB [1-ui8 ] 01 [.]
63: BCHF [1-ui8 ]
64: BCHG [1-ui8 ]
65: BCHL [1-ui8 ]
66: BCHO [1-ui8 ] 1f [.]
67: BCHP [1-ui8 ] 0d [.]
68: BCHR [1-ui8 ] 3a [:]
69: BCHT [1-ui8 ] 06 [.]
70: BCHX [1-ui8 ] 01 [.]
71: BCLM [1-ui8 ] 64 [d]
72: BEZL [1-ui8 ] 00 [.]
73: BILB [1-ui8 ] 1f [.]
74: BILO [2-ui8 ] 1f12 [..]
75: BNCM [1-ui8 ]
76: BNCR [1-ui8 ] 01 [.]
77: BNum [1-ui8 ] 01 [.]
78: BRSC [2-ui16] 005f [._]
79: BSAC [1-ui8 ] 00 [.]
80: BSIn [1-ui8 ] 40 [@]
81: BTIL [2-ui16] 0780 [..]
82: BTTI [1-ui8 ] 02 [.]
83: BTVI [1-ui8 ] 03 [.]
84: BTVR [1-ui8 ] 01 [.]
85: BTVT [1-ui8 ] 01 [.]
86: CH2S [1-flag] 00 [.]
87: CHBI [2-ui16] 0000 [..]
88: CHBV [2-ui16] 3138 [18]
89: CHGC [2-ui16] 0000 [..]
90: CHGD [1-flag]
91: CHGI [2-ui16] 0080 [..]
92: CHGV [2-ui16] 3130 [10]
93: CHPV [2-si16] 3130 [10]
94: CLK! [1-ui8 ] 00 [.]
95: CLKC [10-{clc] 00000e1000000e10198c [..........]
96: CLKH [8-{clh] 0000708000011940 [..p....@]
97: CLKS [2-fp1f] 8000 [..]
98: CLKT [4-ui32] 0001086c [...l]
99: CLSD [2-ui16] 0000 [..]
100: CLWK [2-ui16] 0076 [.v]
101: CRCB [4-ui32] f0255a54 [.%ZT]
102: CRCU [4-ui32]
103: DPLM [3-{lim]support.apple.com/kb/HT3964?viewlocale=en_US
104: EPCA [4-ui32] 00007000 [..p.]
105: EPCF [1-flag] 01 [.]
106: EPCI [4-ui32] 03e00700 [....]
107: EPCV [2-ui16] 0001 [..]
108: EPMA [4-ch8*] 00006080 [..`.]
109: EPMI [1-ui8 ] 00 [.]
110: EPUA [4-ui32] 00006000 [..`.]
111: EPUF [1-flag] 01 [.]
112: EPUI [4-ui32] 03e00001 [....]
113: EPUV [2-ui16] 0001 [..]
114: EVCT [2-ui16] 0000 [..]
115: EVMD [4-ui32]
116: EVRD [32-ch8*] 2303fa0001014a8d2304fa0001014a8df60601000000d83c760600000200858e [#.....J.#.....J........<v.......]
117: F0Ac [2-fpe2] 2edc [..]
118: F0ID [16-{fds] 00010c004c6566742073696465202000 [....Left side .]
119: F0Mn [2-fpe2] 2ee0 [..]
120: F0Mt [2-ui16] f400 [..]
121: F0Mx [2-fpe2] 5910 [Y.]
122: F0Tg [2-fpe2] 2ee0 [..]
123: FNum [1-ui8 ] 01 [.]
124: FPhz [2-si16]
125: FS! [2-ui16] 0000 [..]
126: HBWK [1-flag] 00 [.]
127: HDBS [1-ui8 ] 00 [.]
128: HDST [4-hex_] 00000000 [....]
129: HDSW [4-hex_] 0dcd0db2 [....]
130: IBIR [2-fp2e] 0000 [..]
131: IBIr [2-ui16] 0000 [..]
132: IC0C [2-fp6a] 0e2c [.,]
133: IC1C [2-fp4c] 0776 [.v]
134: ID0R [2-fp3d] 0000 [..]
135: ID0r [2-ui16] 0000 [..]
136: ID1R [2-fp6a] 0000 [..]
137: ID1r [2-ui16] 0000 [..]
138: IH0C [2-fp4c] 0000 [..]
139: IH0r [2-ui16] 0000 [..]
140: IN0R [2-fp6a] 07c9 [..]
141: IN1R [2-fp6a] 00e6 [..]
142: IO0C [2-fp4c] 0000 [..]
143: IO0r [2-ui16] 0000 [..]
144: IP0R [2-fp4c] 1df8 [..]
145: IP0r [2-ui16] 3500 [5.]
146: IW0C [2-fp4c] 0000 [..]
147: IW0r [2-ui16] 0000 [..]
148: LAcN [1-ui8 ]
149: LAtN [2-ui16]
150: LCCN [1-ui8 ] 41 [A]
151: LCCQ [1-ui8 ] 5f [_]
152: LCKA [1-ui8 ] 61 [a]
153: LCSA [1-ui8 ] 0f [.]
154: LCTN [1-ui8 ] 7b [{]
155: LCTQ [1-ui8 ] a2 [.]
156: LDSP [1-flag]
157: LKSB [2-{lkb]
158: LS! [1-ui8 ] 00 [.]
159: LSCF [10-{lsc] 00c80190800002020020 [......... ]
160: LSDD [8-{lsd]
161: LSDU [8-{lsd] 0003000200140003 [........]
162: LSFD [6-{lsf] 00000004008c [......]
163: LSFU [6-{lsf] 00000004008c [......]
164: LSLB [2-{pwm] ffff [..]
165: LSLF [2-{pwm] 0000 [..]
166: LSLN [2-{pwm] ffff [..]
167: LSOF [1-flag] 01 [.]
168: LSOO [1-flag]
169: LSPV [2-{pwm] 0000 [..]
170: LSRB [1-flag]
171: LSSB [2-{lso]
172: LSSE [1-flag] 01 [.]
173: LSSS [2-{lso]
174: LSSV [2-ui16] ffff [..]
175: LSUP [1-ui8 ]
176: MACA [4-ui32] 00000000 [....]
177: MACM [1-flag] 01 [.]
178: MACR [32-ch8*]
179: MOCF [2-ui16] 8300 [..]
180: MOCN [2-ui16] e0f8 [..]
181: MOHD [1-ui8 ] 14 [.]
182: MOHT [2-sp78] 01c0 [..]
183: MOLD [1-ui8 ] 14 [.]
184: MOLT [2-sp78] 0060 [.`]
185: MOST [2-ui16] 8003 [..]
186: MOVX [2-sp78] 0003 [..]
187: MOVY [2-sp78] 0003 [..]
188: MOVZ [2-sp78] 0105 [..]
189: MO_X [2-sp78] 0002 [..]
190: MO_Y [2-sp78] 0000 [..]
191: MO_Z [2-sp78] 0105 [..]
192: MSAL [1-ui8 ] 4b [K]
193: MSAR [2-ui16] 0000 [..]
194: MSAc [2-fp88] 0000 [..]
195: MSAg [2-fp88] 0000 [..]
196: MSAm [2-fp88] 0000 [..]
197: MSBC [2-ui16] 01fb [..]
198: MSBP [2-ui16] 1250 [.P]
199: MSBc [2-ui16] 0000 [..]
200: MSBp [2-ui16] 0fe4 [..]
201: MSDI [1-flag] 00 [.]
202: MSDW [1-flag]
203: MSFG [1-ui8 ] 00 [.]
204: MSLD [1-ui8 ] 00 [.]
205: MSPA [2-fp6a] 0000 [..]
206: MSPC [1-ui8 ] 06 [.]
207: MSPS [2-ui16] 0001 [..]
208: MSPZ [1-ui8 ] 08 [.]
209: MSPs [2-ui16] 0000 [..]
210: MSSD [1-si8 ] 03 [.]
211: MSSE [2-ui16] 0000 [..]
212: MSSF [4-ui32] 00000001 [....]
213: MSSP [1-si8 ] 05 [.]
214: MSSS [1-{mss] 00 [.]
215: MSTC [2-ui16] 0000 [..]
216: MSTM [1-ui8 ] 01 [.]
217: MSTc [1-ui8 ] 00 [.]
218: MSTg [1-ui8 ] 00 [.]
219: MSTm [1-ui8 ] 00 [.]
220: MSWR [1-ui8 ]
221: MSXC [4-ch8*] 00000000 [....]
222: MSXD [16-ch8*] 00000000000000000000000000000000 [................]
223: MSXK [32-ch8*] 0102030405060708090a0b0c0d0e0f1011120000000000000000000000000000 [................................]
224: MSXN [1-ui8 ] 12 [.]
225: MSXS [4-ch8*] 0205070a [....]
226: MSXb [1-ui8 ] 00 [.]
227: MSXc [4-ch8*] 00000000 [....]
228: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
229: MSXk [32-ch8*] 21222324f0f1f2f3000000000000000000000000000000000000000000000000 [!"#$............................]
230: MSXm [2-ui16] 0008 [..]
231: MSXn [1-ui8 ] 28 [(]
232: MSXs [4-ui32] 0103060c [....]
233: NACK [1-flag]
234: NATJ [1-ui8 ] 00 [.]
235: NATi [2-ui16] 0000 [..]
236: NOPB [1-ui8 ] 00 [.]
237: NTOK [1-ui8 ]
238: ONMI [1-ui8 ] 00 [.]
239: OWCT [2-ui16] 0010 [..]
240: PBIC [2-fp88] 0000 [..]
241: PC0C [2-fp88] 02e3 [..]
242: PC1C [2-fp88] 0486 [..]
243: PD0R [2-fp88] 0000 [..]
244: PD1R [2-fp88] 0000 [..]
245: PH0C [2-fp88] 0000 [..]
246: PHPC [2-fp88] 06c9 [..]
247: PN0R [2-fp88] 01ec [..]
248: PN1R [2-fp88] 0056 [.V]
249: PO0C [2-fp88] 0000 [..]
250: PP0R [2-fp88] 148c [..]
251: PTHC [2-fp88] 20fb [ .]
252: PW0C [2-fp88] 0000 [..]
253: RBr [8-ch8*] 6b31396900000000 [k19i....]
254: REV [6-{rev] 01490f000002 [.I....]
255: RMde [1-char] 41 [A]
256: RPlt [8-ch8*] 6b31396900000000 [k19i....]
257: RSvn [4-ui32] 00006446 [..dF]
258: RVBF [6-{rev] 01490f000002 [.I....]
259: RVUF [6-{rev] 01490f000002 [.I....]
260: SAS! [4-hex_]
261: SBS! [2-ui16]
262: SCIA [2-ui16] 03f8 [..]
263: SCIL [1-ui8] 00 [.]
264: SDRd [2-ui16]
265: SIP [1-ui8] 01 [.]
266: SIS! [2-hex_]
267: SIT! [2-hex_]
268: SM0x [2-ui16] 7fc0 [..]
269: SM0y [2-ui16] 7f80 [..]
270: SM0z [2-ui16] b400 [..]
271: SMBC [5-ch8*]
272: SMBG [1-ui8 ]
273: SMBR [32-ch8*]
274: SMBS [2-ch8*]
275: SMBW [32-ch8*]
276: SPH0 [2-ui16] 2a60 [*`]
277: SPHS [1-ui8 ] 00 [.]
278: SPHT [1-ui8 ] 00 [.]
279: SPHZ [1-ui8]
280: SPS! [2-ui16]
281: TB0T [2-sp78] 19b3 [..]
282: TB1T [2-sp78] 19b3 [..]
283: TB2T [2-sp78] 1933 [.3]
284: TB3T [2-sp78] 0000 [..]
285: TC0D [2-sp78] 2b20 [+ ]
286: TC0F [2-sp78] 248c [$.]
287: TC0P [2-sp78] 2500 [%.]
288: TN0D [2-sp78] 29a0 [).]
289: TN0P [2-sp78] 23e0 [#.]
290: TTF0 [2-sp78] 3100 [1.]
291: Th2H [2-sp78] 2180 [!.]
292: Ts0P [2-sp78] 1910 [..]
293: Ts0S [2-sp78] 1f78 [.x]
294: UPRC [2-ui16] 0845 [.E]
295: VBOC [2-fp6a] 0000 [..]
296: VBOc [2-ui16] 0000 [..]
297: VC0C [2-fp2e] 4259 [BY]
298: VC0c [2-ui16] 49c0 [I.]
299: VN0R [2-fp2e] 3fff [?.]
300: VN0r [2-ui16] 4d80 [M.]
301: VO0C [2-fp4c] 0000 [..]
302: VO0r [2-ui16] 0000 [..]
303: VP0R [2-fp4c] bf4b [.K]
304: VP0r [2-ui16] 9b00 [..]
305: VW0C [2-fp4c] 0000 [..]
306: VW0r [2-ui16] 0000 [..]
307: zDBG [1-ui8] 00 [.]



```

The good thing is, people who run linux are not generally entirely stupid, so they are aware of the temperature at least ... but to me, this is quite an important to make linux fesible for macbook pro users.  I set my min speed to 3000rpm which is still relatively quiet, and then keep an eye on the temperature sensors. Obviously this is a temporary solution :)

---

### Post by kosumi68 on 2010-04-26
> 
... and now intermittently i get errors reading from TG0T GPU transistor..


The TG0T is one of the nonexisting registers on the MBP5,4 that the provided applesmc DKMS package stopped trying to read. Are you perhaps still running the old applesmc module, or do you have a program reading that register, or did the module not properly recognize your model? Perhaps a
```

rmmod applesmc;
modprobe applesmc;
dmesg | grep applesmc:

```
will reveal what model is detected.

---

### Post by m.prebble on 2010-04-26
That is probably the reason. I have libsensors and a gnome applet that displays temps on the status bar. Here is dmesg output:

```
[12163.540654] applesmc: driver unloaded.
[12180.099812] applesmc: Apple MacBook Pro 5 detected:
[12180.099819] applesmc:  - Model with accelerometer
[12180.099823] applesmc:  - Model with light sensors and backlight
[12180.099828] applesmc:  - Model with 20 temperature sensors
[12180.100786] applesmc: device has already been initialized (0xe0, 0xf8).
[12180.100791] applesmc: device successfully initialized.
[12180.110830] applesmc: 1 fans found.
[12180.114014] applesmc: driver successfully loaded.
[12180.541169] applesmc: light sensor data length set to 10
[12181.883072] applesmc: wait status failed: 5 != 0



```

---

### Post by kosumi68 on 2010-04-26
It should actually say "Apple MacBook Pro 5,4 detected", it is falling back to the MacBookPro5 model. To know if the dkms package got properly installed, the "modprobe -l | grep applesmc" should point to updates/dkms/applesmc.ko rather than to the kernel module tree.

---

### Post by m.prebble on 2010-04-26
marcus@marcus-ubuntu:~$ modprobe -l | grep applesmc
updates/dkms/applesmc.ko

---

### Post by kosumi68 on 2010-04-27
Puzzling. If "grep MacBookPro5 /usr/src/applesmc-0.15.1/applesmc.c" reports the 5,4 line, there is something wrong with the patch I just cannot see. For the record, posting the exact product name from dmidecode could help as well.

---

### Post by kosumi68 on 2010-04-29
Was the MacBookPro5,4 issue resolved? I need a confirmation that it works before the needed change can propagate any further.

---

### Post by bye on 2010-04-29
HI kosumi68, My MacBookPro5,3 has a similar problem: the fans stay at 2000  most of time until the cpu temperatures go up to  ~78 degrees, then the fans speed up to 3200rpm gradually and cpu temperatures stay at about 72~75 degrees. Is this normal?

---

### Post by kosumi68 on 2010-04-30
Thanks for the data! Please find enclosed a DKMS package to test. Uncompress, install (double-click on the .deb file), reboot. "dmesg | grep applesmc:" should read "Apple MacBook Pro 5,3 detected:" in your case. Please confirm. Thanks!

EDIT: to answer you question, yes it seems normal for the 2007-2008 type models, and many users report that this setup works fine for them. (It does however mean that the smc-check-fan-safe.sh makes the wrong assumption regarding the MBP53 model.)

EDIT2: and the attached package can be found at [http://ubuntuforums.org/showpost.php?p=9199384&postcount=24](http://ubuntuforums.org/showpost.php?p=9199384&postcount=24) -- I was apparently in a hurry this morning ;-)

---

### Post by bye on 2010-04-30
Yes, it reports the correct model after loading the new module

```

[   25.894059] applesmc: Apple MacBook Pro 5,3 detected:
[   25.894061] applesmc:  - Model with accelerometer
[   25.894063] applesmc:  - Model with light sensors and backlight
[   25.894064] applesmc:  - Model with 19 temperature sensors
[   25.897015] applesmc: device has already been initialized (0xe0, 0x00).
[   25.897016] applesmc: device successfully initialized.
[   25.899475] applesmc: 2 fans found.
[   25.911453] input: applesmc as /devices/platform/applesmc.768/input/input7
[   25.911575] applesmc: driver successfully loaded.
[  535.504990] applesmc: light sensor data length set to 10
[  686.679002] applesmc: wait status failed: 5 != 1

```

The output of applesmc-test.sh

```

accelerometer: present, readable, output: (18,-8,-280)
fan:           present, readable, output: 2000
light:         present, readable, output: (0,0)
leds:          present,
 led:                   readable, output: 100
temperatures:  present,
 temperature:           readable, output: 48500
 temperature:           readable, output: 54500
 temperature:           readable, output: 57500
 temperature:           readable, output: 59500
 temperature:           readable, output: 56500
 temperature:           readable, output: 49000
 temperature:           readable, output: 53000
 temperature:           readable, output: 55500
 temperature:           readable, output: 33000
 temperature:           readable, output: 44750
 temperature:           readable, output: 36250
 temperature:           readable, output: 36250
 temperature:           readable, output: 34750
 temperature:           readable, output: 0
 temperature:           readable, output: 59500
 temperature:           readable, output: 54500
 temperature:           readable, output: 54750
 temperature:           readable, output: 63000
 temperature:           readable, output: 56000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      41

```

---

### Post by kosumi68 on 2010-04-30
Excellent! Version 0.15.2 of applesmc-dkms has been uploaded to the mactel PPA for karmic and lucid, with temperature sensor support for MBP5,3, MBP5,4, MBP6 and MBP7. Thanks!

---

### Post by linuxopjemac on 2010-05-02
Good work kosumi68 !

---

### Post by bluenode on 2010-05-05
This eliminated the message:
"applesmc: wait status failed: 4 != 0"
appearing on my MacBook 4.1, Lucid install.  

Thanks very much!

---

### Post by undoIT on 2010-05-08
I have the Macbook 5,1 with Nvidia 9400m and the GPU regularly overheats whenever I am doing anything system intensive or if there is inadequate airflow under the laptop. I have sensor applet installed and if the GPU is running above 65 degrees celsius for an extended period of time (not that long) then the system freezes up. This happened yesterday while installing an OS in VirtualBox. I came back and Ubuntu was frozen half way thru the install and the GPU was reading 68 degrees. Usually, before it freezes, the screen may flicker slightly, like the graphics card is getting ready to crap out. Then a minute or two later, it freezes.

I opened the case last night for the first time in almost two years and there was hardly any dust in the fan / cooling, wasn't even worth cracking it open but I blew it out anyways. Do I just have a flaky Nvidia GPU that can't take the heat? Or is it actually overheating? Currently, it is idling at 55 degrees, core 1 and 2 are at 47 degrees. Also, it seems that the fans never go higher than 2000 rpm. Shouldn't they ramp up as heat increases?

---

### Post by kosumi68 on 2010-05-08
Hi undoit,

I am sure you are aware of the "set fan1_manual to zero" issue, so there could be a problem with your hardware. There are many reports from "genuine" apple users having the same problem in OSX. Could be memory, could be battery, could be heat paste poorly applied, for instance.

And yes, it should ramp up, but on newer macbooks it does not happen until around 85-95 degC -- and that is true also in OSX without special fan control.

---

### Post by undoIT on 2010-05-08
> **kosumi68 said:**
> Hi undoit,

I am sure you are aware of the "set fan1_manual to zero" issue, so there could be a problem with your hardware. There are many reports from "genuine" apple users having the same problem in OSX. Could be memory, could be battery, could be heat paste poorly applied, for instance.

And yes, it should ramp up, but on newer macbooks it does not happen until around 85-95 degC -- and that is true also in OSX without special fan control.

Thanks Kosumi, I have already tested the memory. I guess fan speed isn't the issue. And yes, I've had it freeze up in OS X as well, I just hardly ever use OS X.

Makes me wish I had gotten the 3 year Applecare :(

---

### Post by undoIT on 2010-05-10
I'm using sensors-applet to monitor temperatures. There is a way to adjust the properties so that a command is fired when the sensor high value is hit. Is there a way to fire off the command to adjust fan speed with this? I'm not sure how to do this since the command requires sudo.

Fan speed command:

```
echo 4000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
```

---

### Post by undoIT on 2010-05-12
> **undoIT said:**
> I have the Macbook 5,1 with Nvidia 9400m and the GPU regularly overheats whenever I am doing anything system intensive or if there is inadequate airflow under the laptop. I have sensor applet installed and if the GPU is running above 65 degrees celsius for an extended period of time (not that long) then the system freezes up. This happened yesterday while installing an OS in VirtualBox. I came back and Ubuntu was frozen half way thru the install and the GPU was reading 68 degrees. Usually, before it freezes, the screen may flicker slightly, like the graphics card is getting ready to crap out. Then a minute or two later, it freezes.

I opened the case last night for the first time in almost two years and there was hardly any dust in the fan / cooling, wasn't even worth cracking it open but I blew it out anyways. Do I just have a flaky Nvidia GPU that can't take the heat? Or is it actually overheating? Currently, it is idling at 55 degrees, core 1 and 2 are at 47 degrees. Also, it seems that the fans never go higher than 2000 rpm. Shouldn't they ramp up as heat increases?

Well, I made a nice discovery regarding the overheating issue. After installing some of the latest updates, I couldn't boot into Lucid anymore without the low graphics mode error. I searched around for some hacks and nothing I tried worked. So, I decided to try installing the 173 driver as a last resort.

Wow! Not only is the low graphics mode error gone, the Macbook doesn't freeze anymore! I've done several tests now. Yesterday I ran glxgears and a youtube video simultaneously to get the GPU up to a toasty 84 degrees celsius and the CPU cores above 80 degrees. Also got the fan RPMs maxed out at 6000 for the first time ever. After 20 minutes, no freezing.

Later in the evening, I tried the same thing for another hour. Again no freezes. This morning, I ran it through the paces for 2 hours straight, the GPU settled into 75 degrees and the CPUS were around 80. No freezes. Not even a screen flicker.

So, it seems to me that the 18x and 19x Nvidia drivers for Linux (and perhaps the drivers for OS X) are to blame when it comes to the 9400m card causing system freezes. I haven't tested OS X recently, but I had it lock up on me 5 or 6 times in the past with some pink and green screen artifacts. That is a lot of freezes considering that I rarely use OS X.

What is unfortunate is that it is highly doubtful this will get fixed, since the 9400m is an older card, the Nvidia drivers are proprietary, and Nvidia has clearly stated that they have no interest in supporting Linux / open source drivers. I made a decision recently not to purchase any laptops with Nvidia cards because of these issues. I have just had way too many problems with their cards and I don't like their policy regarding open source software.

It is also a shame that Apple doesn't offer any laptops without Nvidia cards.

---

### Post by kosumi68 on 2010-05-13
Excellent. What about the noveau? I am not running nVidia myself, so I am asking out of curiosity.

---

### Post by alexmurray on 2010-05-13
@undoIT: you should send an email to the Nvidia developers [email]linux-bugs@nvidia.com[/email] and post a bug report on their forums - they're usually pretty responsive to issues I've notified them of in the past for their binary drivers - see here for more info [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) and from the [README]("http://us.download.nvidia.com/XFree86/Linux-x86_64/195.36.24/README/README.txt")

> When emailing [email]linux-bugs@nvidia.com[/email],
please include the 'nvidia-bug-report.log.gz' file generated by the
'nvidia-bug-report.sh' script (which is installed as part of driver
installation).

---

### Post by undoIT on 2010-05-13
> **kosumi68 said:**
> Excellent. What about the noveau? I am not running nVidia myself, so I am asking out of curiosity.

I'm really rooting for noveau. However, with the current noveau driver on the MacBook 5,1 the CPU cores run a lot hotter, the GPU thermal sensor is not detected, 3D acceleration is not supported and there may be other issues I'm not aware of. However, the correct resolution is set and there was no hack needed for plymouth.

If the noveau driver can match the functionality of the proprietary driver, minus all the bugs, I'd have no problem with Nvidia cards. I just wish Nvidia would cooperate and collaborate with the noveau team.

---

### Post by onejdev on 2010-07-29
hate to do this, but even after reading a lot of great info in this thread and applying what I thought would fix this, I am having some errors on an MacPro running Lucid.   /var/log/messages is littered with the following errors:

applesmc: wait status failed: 5 != 0

I ran the applesmc-test.sh script and this is the result:

```

model: MacPro1,1

accelerometer: not present
fan:           present, readable, output: 500
light:         not present
leds:          not present
temperatures:  present,
 temperature:           not readable
 temperature:           readable, output: 50000
 temperature:           not readable
 temperature:           readable, output: 0
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 35000
 temperature:           readable, output: 35000
 temperature:           readable, output: 34000
 temperature:           readable, output: 32500
 temperature:           readable, output: 28000
 temperature:           readable, output: 50000
 temperature:           readable, output: 57500
 temperature:           readable, output: 58500
 temperature:           readable, output: 40000
 temperature:           readable, output: 66000
 temperature:           readable, output: 47000
 temperature:           readable, output: 68000
 temperature:           readable, output: 47000
 temperature:           readable, output: 65000
 temperature:           readable, output: 62000
 temperature:           not readable
 temperature:           readable, output: 40000
 temperature:           readable, output: 67000
 temperature:           readable, output: 47000
 temperature:           readable, output: 67000
 temperature:           readable, output: 67000
 temperature:           readable, output: 35500
 temperature:           readable, output: 31000
 temperature:           not readable
 temperature:           readable, output: 32000
 temperature:           readable, output: 49000
 temperature:           not readable
 temperature:           readable, output: 40000
 temperature:           readable, output: 0
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      3

smc-fan:  Mt Sf type B

```

Here is the result of the scan-smc.sh script also

```

0: #KEY [4-ui32] 000000ff [....]
1: +LKS [1-flag] 07 [.]
2: ACID [8-ch8*] 0000000000000000 [........]
3: ALSC [16-{alc] 0192009608b00002000100640ed90000 [...........d....]
4: AUPO [1-ui8 ] 00 [.]
5: BATP [1-flag] 00 [.]
6: BISE [1-ui8 ]
7: BNum [1-ui8 ] 00 [.]
8: BRSC [2-ui16] 0000 [..]
9: CLK! [1-ui8 ] 00 [.]
10: CLKC [10-{clc] 00000e1000000e10198c [..........]
11: CLKH [8-{clh] 0000000000000000 [........]
12: CLKS [2-fp1f] 8000 [..]
13: CLKT [4-ui32] 00013e65 [..>e]
14: CONT [4-ui32] 16001600 [....]
15: CRCB [4-ui32] c512fc40 [...@]
16: CRCU [4-ui32]
17: Dlpc [1-flag]
18: EPCF [1-flag] 01 [.]
19: EPCI [4-ui32] 00800700 [....]
20: EPCV [2-ui16] 0001 [..]
21: EPMA [4-ch8*] 0000e080 [....]
22: EPMI [1-ui8 ] 00 [.]
23: EPUF [1-flag] 01 [.]
24: EPUI [4-ui32] 00800001 [....]
25: EPUV [2-ui16] 0001 [..]
26: EVCT [2-ui16] 0000 [..]
27: EVMD [4-ui32]
28: EVRD [32-ch8*] f6060300000124f0c101000001000f2b00000000000000000000000000000000 [......$........+................]
29: F0Ac [2-fpe2] 07cd [..]
30: F0ID [16-{fds] 010001004350555f4d454d2000000000 [....CPU_MEM ....]
31: F0Mn [2-fpe2] 07d0 [..]
32: F0Mt [2-ui16] 01f4 [..]
33: F0Mx [2-fpe2] 2d50 [-P]
34: F0Sf [2-fpe2] 12c0 [..]
35: F0Tg [2-fpe2] 07d0 [..]
36: F1Ac [2-fpe2] 07d1 [..]
37: F1ID [16-{fds] 01010400494f20000000000000000000 [....IO .........]
38: F1Mn [2-fpe2] 07d0 [..]
39: F1Mt [2-ui16] 0252 [.R]
40: F1Mx [2-fpe2] 2d50 [-P]
41: F1Sf [2-fpe2] 12c0 [..]
42: F1Tg [2-fpe2] 07d0 [..]
43: F2Ac [2-fpe2] 095a [.Z]
44: F2ID [16-{fds] 01000d00455848415553542000000000 [....EXHAUST ....]
45: F2Mn [2-fpe2] 07d0 [..]
46: F2Mt [2-ui16] 0258 [.X]
47: F2Mx [2-fpe2] 2d50 [-P]
48: F2Sf [2-fpe2] 12c0 [..]
49: F2Tg [2-fpe2] 0960 [.`]
50: F3Ac [2-fpe2] 0b3c [.<]
51: F3ID [16-{fds] 01021000505320202000000000000000 [....PS .......]
52: F3Mn [2-fpe2] 0b40 [.@]
53: F3Mt [2-ui16] 035c [.\]
54: F3Mx [2-fpe2] 2bc0 [+.]
55: F3Sf [2-fpe2] 12c0 [..]
56: F3Tg [2-fpe2] 0b40 [.@]
57: FNum [1-ui8 ] 04 [.]
58: FPhz [2-i16 ]
59: FS! [2-ui16] 0000 [..]
60: HDBS [1-ui8 ] 01 [.]
61: HDST [4-ui16] 00000000 [....]
62: HDSW [4-ui32] 00000000 [....]
63: ICAC [2-fp88] 088a [..]
64: ICAc [2-ui16] 1900 [..]
65: ICBC [2-fp88] 092f [./]
66: ICBc [2-ui16] 1b00 [..]
67: IM1s [2-ui16] 2e80 [..]
68: IM2s [2-ui16] 2680 [&.]
69: IMAS [2-fp88] 0269 [.i]
70: IMBS [2-fp88] 01f8 [..]
71: IN0C [2-fp88] 0db9 [..]
72: IN0c [2-ui16] 7d40 [}@]
73: Ie1S [2-fp88] 009e [..]
74: Ie1s [2-ui16] 0c40 [.@]
75: Ie2S [2-fp88] 0010 [..]
76: Ie2s [2-ui16] 0100 [..]
77: Ie3S [2-fp88] 000d [..]
78: Ie3s [2-ui16] 0100 [..]
79: Ie4S [2-fp88] 0006 [..]
80: Ie4s [2-ui16] 0080 [..]
81: IeAS [2-fp88] 000d [..]
82: IeAs [2-ui16] 0100 [..]
83: IeBS [2-fp88] 0009 [..]
84: IeBs [2-ui16] 00c0 [..]
85: Ip0C [2-fp88] 0d78 [.x]
86: Ip0c [2-ui16] 035e [.^]
87: Jp0D [2-ui16] 0000 [..]
88: Jp0S [2-ui16] 0000 [..]
89: Jp0W [2-ui16] 0000 [..]
90: JpFE [1-flag] 01 [.]
91: LAcN [1-ui8 ]
92: LAtN [2-ui16]
93: LS! [1-ui8 ] 00 [.]
94: LSCF [10-{lsc] 02ee0190800001020006 [..........]
95: LSDD [8-{lsd] 0002000300030019 [........]
96: LSDU [8-{lsd] 0003000200140003 [........]
97: LSFD [6-{lsf] 00000004001e [......]
98: LSFU [6-{lsf] 17700007003c [.p...<]
99: LSLB [2-{pwm] ffff [..]
100: LSLF [2-{pwm] 0000 [..]
101: LSLN [2-{pwm] 4e20 [N ]
102: LSOF [1-flag] 00 [.]
103: LSOO [1-flag]
104: LSPV [2-{pwm] 4e20 [N ]
105: LSRB [1-flag]
106: LSSB [2-{lso]
107: LSSE [1-flag] 01 [.]
108: LSSS [2-{lso]
109: LSSV [2-ui16] ffff [..]
110: LSUP [1-ui8 ]
111: MACA [4-ui32] 00000000 [....]
112: MACM [1-flag] 01 [.]
113: MACR [32-ch8*] 6368382a900124f0c101000001000f2b00000000000000000000000000000000 [ch8*..$........+................]
114: MDE [2-ui16] 00ff [..]
115: MDLC [2-ui16] 0000 [..]
116: MDSS [1-ui8 ] 02 [.]
117: MOCF [2-ui16] 0000 [..]
118: MSAL [1-si8 ]
119: MSDW [1-flag]
120: MSLD [1-ui8 ] 00 [.]
121: MSPS [1-{msp] 00 [.]
122: MSSD [1-si8 ] 03 [.]
123: MSSS [1-{mss] 00 [.]
124: MSTM [1-ui8 ] 00 [.]
125: MSWR [1-ui8 ]
126: NATJ [1-ui8 ] 00 [.]
127: NATi [2-ui16] 0000 [..]
128: NTOK [1-ui8 ]
129: NVPR [1-ui8 ] 00 [.]
130: NVPW [1-ui8 ]
131: ONMI [1-ui8 ] 00 [.]
132: OSK0 [32-ch8*] 6f757268617264776f726b62797468657365776f72647367756172646564706c [ourhardworkbythesewordsguardedpl]
133: OSK1 [32-ch8*] 65617365646f6e74737465616c2863294170706c65436f6d7075746572496e63 [easedontsteal(c)AppleComputerInc]
134: PCAC [2-fp88] 100d [..]
135: PCBC [2-fp88] 0e55 [.U]
136: PMAS [2-fp88] 1c97 [..]
137: PMBS [2-fp88] 173b [.;]
138: PN0C [2-fp88] 1454 [.T]
139: Pe1S [2-fp88] 077c [.|]
140: Pe2S [2-fp88] 009a [..]
141: Pe3S [2-fp88] 009a [..]
142: Pe4S [2-fp88] 0047 [.G]
143: PeAS [2-fp88] 009a [..]
144: PeBS [2-fp88] 0047 [.G]
145: PeTS [2-ui16] 0009 [..]
146: Pp0C [2-fpc4] 0a2b [.+]
147: RBr [8-ch8*] 6d34330000000000 [m43.....]
148: REV [6-{rev] 01070f000008 [......]
149: RMde [1-byte] 41 [A]
150: RPS0 [8-{psh] 0c02060408ce0000 [........]
151: RPlt [8-ch8*] 6d34330000000000 [m43.....]
152: RSvn [4-ui32] 00002721 [..'!]
153: RVBF [6-{rev] 01070f000008 [......]
154: RVUF [6-{rev] 01070f000008 [......]
155: SAS! [4-ui32]
156: SBF [2-ui16] 0000 [..]
157: SDRd [2-ui16]
158: SIS! [2-ui16]
159: SIT! [2-ui16]
160: SIU! [2-ui16]
161: SIV! [2-ui16]
162: SIW! [2-ui16]
163: SPC0 [1-ui8] 04 [.]
164: SPC1 [1-ui8] 01 [.]
165: SPC2 [1-ui8] 00 [.]
166: SPH0 [2-ui16] 0000 [..]
167: SPH1 [2-ui16] 0000 [..]
168: SPHS [1-ui8 ] 00 [.]
169: SPHT [1-ui8 ] 00 [.]
170: SPS! [2-ui16]
171: TA0P [2-sp78] 1c00 [..]
172: TC0C [2-sp78] 2f00 [/.]
173: TC0P [2-sp78] 2810 [(.]
174: TC1C [2-sp78] 0000 [..]
175: TC2C [2-sp78] 2f00 [/.]
176: TC3C [2-sp78] 0000 [..]
177: TCAH [2-sp78] 1f90 [..]
178: TCBH [2-sp78] 2090 [ .]
179: TH0P [2-sp78] 2320 [# ]
180: TH1P [2-sp78] 22e0 [".]
181: TH2P [2-sp78] 2220 [" ]
182: TH3P [2-sp78] 2080 [ .]
183: TM0P [2-sp78] 2900 [).]
184: TM0S [2-sp78] 4280 [B.]
185: TM1P [2-sp78] 2f00 [/.]
186: TM1S [2-sp78] 4500 [E.]
187: TM2P [2-sp78] 2f00 [/.]
188: TM2S [2-sp78] 4180 [A.]
189: TM3S [2-sp78] 3e00 [>.]
190: TM8P [2-sp78] 2800 [(.]
191: TM8S [2-sp78] 4300 [C.]
192: TM9P [2-sp78] 2f00 [/.]
193: TM9S [2-sp78] 4380 [C.]
194: TMAP [2-sp78] 3200 [2.]
195: TMAS [2-sp78] 3a00 [:.]
196: TMBS [2-sp78] 3a80 [:.]
197: TN0H [2-sp78] 4280 [B.]
198: TS0C [2-sp78] 2380 [#.]
199: Tp0C [2-sp78] 2f00 [/.]
200: Tp1C [2-sp78] 2b90 [+.]
201: Tv0S [2-sp78] 22b0 [".]
202: Tv1S [2-sp78] 2332 [#2]
203: VCAC [2-fp88] 013b [.;]
204: VCAc [2-ui16] 65c0 [e.]
205: VCBC [2-fp88] 013d [.=]
206: VCBc [2-ui16] 58c0 [X.]
207: VM0s [2-ui16] 02ac [..]
208: VM1s [2-ui16] 0198 [..]
209: VM2s [2-ui16] 02f4 [..]
210: VM3s [2-ui16] 0330 [.0]
211: VM4s [2-ui16] 02f8 [..]
212: VM8s [2-ui16] 02ac [..]
213: VM9s [2-ui16] 0198 [..]
214: VMAS [2-fp88] 0bdd [..]
215: VMAs [2-ui16] 02f4 [..]
216: VMBS [2-fp88] 0bcd [..]
217: VMBs [2-ui16] 0334 [.4]
218: VMCs [2-ui16] 02f4 [..]
219: VN0C [2-fp88] 017c [.|]
220: VS2c [2-ui16] 00c4 [..]
221: VS3c [2-ui16] 00bf [..]
222: VS4c [2-ui16] 00bd [..]
223: VS5c [2-ui16] 00bf [..]
224: VS6c [2-ui16] 00d3 [..]
225: VS7c [2-ui16] 00cb [..]
226: VS8c [2-ui16] 00bd [..]
227: VS9c [2-ui16] 00c4 [..]
228: VSAc [2-ui16] 0073 [.s]
229: VSBc [2-ui16] 00af [..]
230: VSCc [2-ui16] 00e9 [..]
231: VSDc [2-ui16] 00c9 [..]
232: VSEc [2-ui16] 00cb [..]
233: VSFc [2-ui16] 00bb [..]
234: VeES [2-fp88] 0be8 [..]
235: Vp0C [2-fp88] 0c12 [..]
236: Vp0c [2-ui16] 0c15 [..]
237: zDBG [1-ui8]
238: zSCI [1-ui8]
239: {clc [3-] 0001db [...]
240: {clf [3-] 0001e0 [...]
241: {clh [3-] 0001db [...]
242: {fds [3-] 0001db [...]
243: {lsc [3-] 0001dd [...]
244: {lsd [3-] 0001db [...]
245: {lsf [3-] 0001db [...]
246: {lsm [3-] 0001dd [...]
247: {lso [3-] 0001dd [...]
248: {lss [3-] 0001dd [...]
249: {msp [3-] 0001df [...]
250: {mss [3-] 0001df [...]
251: {psh [3-] 0001df [...]
252: {pwm [3-] 0001dc [...]
253: {rev [3-] 0001e0 [...]
254: {sds [3-] 0001db [...]

```

Any help anyone could offer would be greatly appreciated.

---

### Post by xeno74 on 2010-08-08
Mac Pro 2009 info :)

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/Mac_Pro_Tower.jpg/300px-Mac_Pro_Tower.jpg[/IMG]

***sudo dmidecode -s system-product-name***

```
MacPro4,1
```***sudo ./applesmc-test.sh***

```
model: MacPro4,1

accelerometer: not present
fan:           present, readable, output: 838
light:         not present
leds:          not present
temperatures:  present,
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 58000
 temperature:           not readable
 temperature:           readable, output: 29000
 temperature:           readable, output: 31000
 temperature:           readable, output: 31750
 temperature:           readable, output: 28500
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 36250
 temperature:           not readable
 temperature:           readable, output: 38250
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 80000
 temperature:           readable, output: 129000
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 47000
 temperature:           not readable
 temperature:           readable, output: 47750
 temperature:           readable, output: 80000
 temperature:           readable, output: 129000
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
performance:   reading all temperatures

 
 fail frequency:        1.000
 reads per second:      1

smc-fan:  Mt type C


```

Cheers,

Christian

---

### Post by davidryderuk on 2010-08-26
Hi,
Thanks for all the work. This is from the latest version of applesmc on my 2010 Macbook.

sudo dmidecode -s system-product-name

```
MacBook 7,1
```

sudo ./applesmc-test.sh

```
model: MacBook7,1

accelerometer: present, readable, output: (1,19,264)
fan:           present, readable, output: 2000
light:         not present
leds:          not present
temperatures:  present,
 temperature:           readable, output: 29500
 temperature:           readable, output: 31250
 temperature:           readable, output: 48000
 temperature:           readable, output: 43500
 temperature:           not readable
 temperature:           readable, output: 41750
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 41750
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      6

smc-fan:  Mt type C

```

sudo ./scan-smc.sh

```
0: #KEY [4-ui32] 0000013d [...=]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 07 [.]
4: ACCL [1-ui8 ]
5: ACEN [1-ui8 ] 01 [.]
6: ACFP [1-flag] 01 [.]
7: ACIC [2-ui16] 0d80 [..]
8: ACID [8-ch8*] 8518cdb0c0031060 [.......`]
9: ACIN [1-flag] 01 [.]
10: ACLM [1-ui8 ] 55 [U]
11: ALRV [2-ui16] 0000 [..]
12: ALSC [16-{alc] 01920096042e0002000100642efd0000 [...........d....]
13: AUPO [1-ui8 ] 00 [.]
14: B0AC [2-si16] 0568 [.h]
15: B0AV [2-ui16] 30f8 [0.]
16: B0Ad [2-ui16] 0000 [..]
17: B0Al [2-ui16] ffff [..]
18: B0Am [1-ui8 ] 10 [.]
19: B0Ar [1-ui8 ] 00 [.]
20: B0As [1-ui8 ] 00 [.]
21: B0At [2-ui16] 0960 [.`]
22: B0Au [2-ui16] 0960 [.`]
23: B0Az [1-ui8 ] 00 [.]
24: B0BI [1-hex_] 51 [Q]
25: B0CM [2-ui16] 0164 [.d]
26: B0CT [2-ui16] 0002 [..]
27: B0FC [2-ui16] 15c4 [..]
28: B0FV [2-ui16] 0201 [..]
29: B0LI [2-ui16] 0f80 [..]
30: B0PS [2-ui16] 0000 [..]
31: B0RI [2-ui16] 0fa0 [..]
32: B0RM [2-ui16] 1429 [.)]
33: B0St [2-ui16] 0080 [..]
34: B0TF [2-ui16] 0021 [.!]
35: BATP [1-flag] 00 [.]
36: BBAD [1-flag] 00 [.]
37: BBIN [1-flag] 01 [.]
38: BC1V [2-ui16] 105b [.[]
39: BC2V [2-ui16] 1050 [.P]
40: BC3V [2-ui16] 104f [.O]
41: BCLM [1-ui8 ] 64 [d]
42: BCMV [2-ui16] 105b [.[]
43: BEMB [1-flag] 01 [.]
44: BFCT [2-ui16] 0000 [..]
45: BNCM [1-ui8 ]
46: BNCR [1-ui8 ] 00 [.]
47: BNum [1-ui8 ] 01 [.]
48: BRSC [2-ui16] 005d [.]]
49: BSAC [1-ui8 ] 33 [3]
50: BSIn [1-hex_] 43 [C]
51: BTIL [2-ui16] 0580 [..]
52: BTTI [1-ui8 ] 02 [.]
53: BTVI [1-ui8 ] 02 [.]
54: BTVR [1-ui8 ] 01 [.]
55: BTVT [1-ui8 ] 01 [.]
56: BWLM [1-ui8 ] 00 [.]
57: CHBI [2-ui16] 0580 [..]
58: CHBV [2-ui16] 3130 [10]
59: CHGC [2-ui16] 0062 [.b]
60: CHGD [1-flag]
61: CHGI [2-ui16] 0580 [..]
62: CHGV [2-ui16] 3130 [10]
63: CHPV [2-si16] 3130 [10]
64: CLK! [1-ui8 ] 00 [.]
65: CLKC [10-{clc] 00000e1000000e10198c [..........]
66: CLKH [8-{clh] 0000708000011940 [..p....@]
67: CLKS [2-fp1f] 8000 [..]
68: CLKT [4-ui32] 0000b115 [....]
69: CLSD [2-ui16] 0905 [..]
70: CLWK [2-ui16] 0000 [..]
71: CRCB [4-ui32] a3da51a6 [..Q.]
72: CRCU [4-ui32]
73: DPLM [3-{lim]
74: EPCA [4-ui32] 00007000 [..p.]
75: EPCF [1-flag] 01 [.]
76: EPCI [4-ui32] 05200700 [. ..]
77: EPCV [2-ui16] 0001 [..]
78: EPMA [4-ch8*] 00006080 [..`.]
79: EPMI [1-ui8 ] 00 [.]
80: EPUA [4-ui32] 00006000 [..`.]
81: EPUF [1-flag] 01 [.]
82: EPUI [4-ui32] 05200001 [. ..]
83: EPUV [2-ui16] 0001 [..]
84: EVCT [2-ui16] 0303 [..]
85: EVMD [4-ui32]
86: EVRD [32-ch8*] f60603000000a5822304f7000101201736c40000010093860000000000000000 [........#..... .6...............]
87: F0Ac [2-fpe2] 1f2e [..]
88: F0ID [16-{fds] 00000a00457868617573742020000000 [....Exhaust ...]
89: F0Mn [2-fpe2] 1f40 [.@]
90: F0Mt [2-ui16] 0000 [..]
91: F0Mx [2-fpe2] 60e0 [`.]
92: F0Tg [2-fpe2] 1f40 [.@]
93: FMAx [2-fpe2] 1fe2 [..]
94: FNum [1-ui8 ] 01 [.]
95: FPVK [1-ui8 ] 03 [.]
96: FPhz [2-si16]
97: FS! [2-ui16] 0000 [..]
98: G3WD [1-flag] 00 [.]
99: HBWK [1-flag] 00 [.]
100: HDBS [1-ui8 ] 01 [.]
101: HDST [4-hex_] 00000000 [....]
102: HDSW [4-hex_] 0040003f [.@.?]
103: IB0R [2-sp5a] 0097 [..]
104: IB0r [2-ui16] 0440 [.@]
105: IC0C [2-sp5a] 199c [..]
106: IC0R [2-sp5a] 0290 [..]
107: IC0c [2-ui16] 0a80 [..]
108: IC0r [2-ui16] 1180 [..]
109: ID0R [2-sp5a] 0900 [..]
110: ID0r [2-ui16] 49c0 [I.]
111: IN0C [2-sp5a] 099a [..]
112: IN0c [2-ui16] 1c40 [.@]
113: IN1C [2-sp5a] 0287 [..]
114: IN1c [2-ui16] 0e80 [..]
115: IZAP [2-sp5a] 8100 [..]
116: IZAp [2-ui16] 8100 [..]
117: IZBL [2-sp5a] 8100 [..]
118: IZBl [2-ui16] 8100 [..]
119: IZHD [2-sp5a] 8100 [..]
120: IZHd [2-ui16] 8100 [..]
121: IZOD [2-sp5a] 8100 [..]
122: IZOd [2-ui16] 8100 [..]
123: LAcN [1-ui8 ]
124: LAtN [2-ui16]
125: LC2D [2-ui16] 5c4d [\M]
126: LC2E [2-ui16] 5c4d [\M]
127: LCCN [1-ui8 ] d8 [.]
128: LCCQ [1-ui8 ] 81 [.]
129: LCKA [1-ui8 ] fc [.]
130: LCSA [1-ui8 ] 28 [(]
131: LCTN [1-ui8 ] 3b [;]
132: LCTQ [1-ui8 ] e4 [.]
133: LDI2 [1-ui8 ] 01 [.]
134: LDSP [1-flag]
135: LEDC [1-ui8 ] 00 [.]
136: LEDT [2-ui16] 8100 [..]
137: LEIC [1-ui8 ] 00 [.]
138: LEID [32-ui16] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
139: LET0 [4-ui32] 00000000 [....]
140: LET1 [4-ui32] 00000000 [....]
141: LET2 [4-ui32] 00000000 [....]
142: LS! [1-ui8 ] 00 [.]
143: LSCF [10-{lsc] 04b0023a800001020001 [...:......]
144: LSDD [8-{lsd] 0002000300030019 [........]
145: LSDU [8-{lsd] 0003000200140003 [........]
146: LSFD [6-{lsf] 2ee000040017 [......]
147: LSFU [6-{lsf] ffff01900320 [..... ]
148: LSLB [2-{pwm] ffff [..]
149: LSLF [2-{pwm] 0000 [..]
150: LSLN [2-{pwm] ffff [..]
151: LSOF [1-flag] 01 [.]
152: LSOO [1-flag]
153: LSPV [2-{pwm] 0000 [..]
154: LSRB [1-flag]
155: LSSB [2-{lso]
156: LSSE [1-flag] 01 [.]
157: LSSS [2-{lso]
158: LSSV [2-ui16] ffff [..]
159: LSUP [1-ui8 ]
160: MACA [4-ui32] 00000000 [....]
161: MACM [1-flag] 01 [.]
162: MACR [32-ch8*]
163: MLEN [1-ui8 ] 00 [.]
164: MLIA [2-ui16] 04c1 [..]
165: MLIR [32-ch8*] 04b804a004a404ac04a804af049f04ab04aa04a804a404a904ae04c104ba04bd [................................]
166: MLSR [2-ui16] 03e8 [..]
167: MLTM [32-ch8*] 5b005b005b005b005a805a805b005b005b005b005b005b005b005b005b005b00 [[.[.[.[.Z.Z.[.[.[.[.[.[.[.[.[.[.]
168: MOCF [2-ui16] 8600 [..]
169: MOCN [2-ui16] e000 [..]
170: MOHC [1-ui8 ] 0f [.]
171: MOHD [1-ui8 ] 0a [.]
172: MOHT [2-sp78] 01e0 [..]
173: MOLD [1-ui8 ] 0a [.]
174: MOLT [2-sp78] 0020 [. ]
175: MOST [2-ui16] a003 [..]
176: MOVX [2-sp78] 0003 [..]
177: MOVY [2-sp78] 0011 [..]
178: MOVZ [2-sp78] 010a [..]
179: MO_X [2-sp78] 0000 [..]
180: MO_Y [2-sp78] 0014 [..]
181: MO_Z [2-sp78] 0108 [..]
182: MSAL [1-ui8 ] 4b [K]
183: MSAb [2-ui16] 0000 [..]
184: MSAc [2-fp88] 0000 [..]
185: MSAf [2-fp6a] 0000 [..]
186: MSAg [2-fp88] 0000 [..]
187: MSAm [2-fp88] 0000 [..]
188: MSBC [2-ui16] 0000 [..]
189: MSBP [2-ui16] 10c2 [..]
190: MSBc [2-ui16] 0000 [..]
191: MSBp [2-ui16] 10c2 [..]
192: MSDI [1-flag] 00 [.]
193: MSDW [1-flag]
194: MSG3 [1-flag] 00 [.]
195: MSLD [1-ui8 ] 00 [.]
196: MSPA [2-fp6a] 0000 [..]
197: MSPC [1-ui8 ] 05 [.]
198: MSPS [2-ui16] 0003 [..]
199: MSSD [1-si8 ] 03 [.]
200: MSSE [2-ui16] 0000 [..]
201: MSSF [4-ui32] 00000000 [....]
202: MSSG [4-ui32] 00000000 [....]
203: MSSP [1-si8 ] c4 [.]
204: MSSS [1-{mss] 00 [.]
205: MSTC [2-ui16] 0001 [..]
206: MSTM [1-ui8 ] 01 [.]
207: MSTc [1-ui8 ] 00 [.]
208: MSTg [1-ui8 ] 00 [.]
209: MSTm [1-ui8 ] 00 [.]
210: MSWR [1-ui8 ]
211: MSXC [4-ch8*] 00000000 [....]
212: MSXD [32-ch8*] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
213: MSXK [32-ch8*] 0102030405060708090a0b0c0d0e0f1011121314151617181900000000000000 [................................]
214: MSXN [1-ui8 ] 19 [.]
215: MSXS [8-ch8*] 0208070a04090103 [........]
216: MSXb [1-ui8 ] 00 [.]
217: MSXc [4-ch8*] 00000000 [....]
218: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
219: MSXk [32-ch8*] 0102030405060708090a0b0c0d0e0f10f0f1f2f3000000000000000000000000 [................................]
220: MSXm [2-ui16] 0008 [..]
221: MSXn [1-ui8 ] 14 [.]
222: MSXs [4-ui32] 01031009 [....]
223: NACK [1-ui8 ]
224: NATJ [1-ui8 ] 00 [.]
225: NATi [2-ui16] 0000 [..]
226: NOPB [1-ui8 ]
227: NTOK [1-ui8 ]
228: ONMI [1-ui8 ] 00 [.]
229: PB0R [2-sp78] 01da [..]
230: PC0C [2-sp78] 07ee [..]
231: PC0R [2-sp78] 0956 [.V]
232: PD0R [2-sp78] 276c ['l]
233: PHPC [2-sp78] 0d31 [.1]
234: PN0C [2-sp78] 02df [..]
235: PN1C [2-sp78] 00fb [..]
236: PTHC [2-sp78] 20e4 [ .]
237: PZAP [2-sp78] 8100 [..]
238: PZBL [2-sp78] 8100 [..]
239: PZHD [2-sp78] 8100 [..]
240: PZOD [2-sp78] 8100 [..]
241: RBr [8-ch8*] 6b38370000000000 [k87.....]
242: REV [6-{rev] 01600f000005 [.`....]
243: RMde [1-char] 41 [A]
244: RPlt [8-ch8*] 6b38370000000000 [k87.....]
245: RSvn [4-ui32] 00000000 [....]
246: RVBF [6-{rev] 01600f000005 [.`....]
247: RVUF [6-{rev] 01600f000005 [.`....]
248: SAS! [4-hex_] 0000ffff [....]
249: SBF [4-hex_] 00000000 [....]
250: SBFC [4-hex_] 00000000 [....]
251: SBFD [4-hex_] 00000000 [....]
252: SBFE [1-flag] 01 [.]
253: SBFF [4-hex_] 00000000 [....]
254: SBFS [4-hex_] 00000000 [....]
255: SBS! [2-ui16]
256: SCIA [2-ui16] 03f8 [..]
257: SCII [1-ui8 ] 00 [.]
258: SCIL [1-ui8 ] 00 [.]
259: SDAF [2-ui16] 0000 [..]
260: SDAS [2-ui16] 0000 [..]
261: SDRd [2-ui16]
262: SFBR [1-ui8 ] 04 [.]
263: SIP [1-ui8] 01 [.]
264: SIS! [2-hex_]
265: SIT! [2-hex_]
266: SIU! [2-hex_]
267: SM0x [2-ui16] 8040 [.@]
268: SM0y [2-ui16] 7c00 [|.]
269: SM0z [2-ui16] 4b00 [K.]
270: SMBC [6-ch8*]
271: SMBG [1-ui8 ]
272: SMBR [32-ch8*]
273: SMBS [2-ch8*]
274: SMBW [32-ch8*]
275: SPH0 [2-ui16] 0000 [..]
276: SPHR [4-ui32] 00000000 [....]
277: SPHS [1-ui8 ] 00 [.]
278: SPHT [2-ui16] 0000 [..]
279: SPHZ [1-ui8]
280: SPS! [4-hex_] 00000000 [....]
281: TB0T [2-sp78] 1f80 [..]
282: TB1T [2-sp78] 1d19 [..]
283: TB2T [2-sp78] 1f80 [..]
284: TC0D [2-sp78] 35e0 [5.]
285: TC0P [2-sp78] 2ca0 [,.]
286: TC0p [2-sp78] 2ca0 [,.]
287: TH0P [2-sp78] 2620 [& ]
288: TN0D [2-sp78] 3300 [3.]
289: TN0P [2-sp78] 2a80 [*.]
290: TN0S [2-sp78] 39c8 [9.]
291: TN1D [2-sp78] 3600 [6.]
292: TN1E [2-sp78] 3600 [6.]
293: TN1F [2-sp78]
294: TN1G [2-sp78] 5a00 [Z.]
295: TN1S [2-sp78] 39c8 [9.]
296: Th1H [2-sp78] 2aa0 [*.]
297: Th1h [2-sp78] 2aa0 [*.]
298: Ts0P [2-sp78] 1d30 [.0]
299: Ts0S [2-sp78] 24ef [$.]
300: Ts0p [2-sp78] 1d30 [.0]
301: UPRC [2-ui16] 0845 [.E]
302: VC0C [2-sp5a] 042d [.-]
303: VC0c [2-ui16] 4cc0 [L.]
304: VN0C [2-sp5a] 0459 [.Y]
305: VN0c [2-ui16] 54c0 [T.]
306: VP0R [2-sp5a] 321c [2.]
307: VP0r [2-ui16] a300 [..]
308: VZAP [2-sp5a] 8100 [..]
309: VZAp [2-ui16] 8100 [..]
310: VZBL [2-sp5a] 8100 [..]
311: VZBl [2-ui16] 8100 [..]
312: VZOD [2-sp5a] 8100 [..]
313: VZOd [2-ui16] 8100 [..]
314: WKEN [1-ui8] 00 [.]
315: zDBG [1-ui8] 00 [.]
316: zRDB [1-flag] 00 [.]

```

---

### Post by kimptoc on 2010-10-24
Hi,

Results for a MacBook Air 11", late 2010 model:

MacBookAir3,1

Attached are the applesmc and scan-smc results.

HTH,
Chris

---

### Post by mayurdange on 2010-11-29
> **davidryderuk said:**
> Hi,
Thanks for all the work. This is from the latest version of applesmc on my 2010 Macbook.

sudo dmidecode -s system-product-name

```
MacBook 7,1
```

.........................................................

**refer the attached module source code...**
added details for macbook 7,1.
someone please submit patch/or tell me where to??

---

### Post by andybotting on 2011-03-08
Details of the MacBookPro8,2 machine attached

cheers

---

### Post by onejdev on 2011-03-28
> **onejdev said:**
> hate to do this, but even after reading a lot of great info in this thread and applying what I thought would fix this, I am having some errors on an MacPro running Lucid.   /var/log/messages is littered with the following errors:

applesmc: wait status failed: 5 != 0

I ran the applesmc-test.sh script and this is the result:

```

model: MacPro1,1

accelerometer: not present
fan:           present, readable, output: 500
light:         not present
leds:          not present
temperatures:  present,
 temperature:           not readable
 temperature:           readable, output: 50000
 temperature:           not readable
 temperature:           readable, output: 0
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 35000
 temperature:           readable, output: 35000
 temperature:           readable, output: 34000
 temperature:           readable, output: 32500
 temperature:           readable, output: 28000
 temperature:           readable, output: 50000
 temperature:           readable, output: 57500
 temperature:           readable, output: 58500
 temperature:           readable, output: 40000
 temperature:           readable, output: 66000
 temperature:           readable, output: 47000
 temperature:           readable, output: 68000
 temperature:           readable, output: 47000
 temperature:           readable, output: 65000
 temperature:           readable, output: 62000
 temperature:           not readable
 temperature:           readable, output: 40000
 temperature:           readable, output: 67000
 temperature:           readable, output: 47000
 temperature:           readable, output: 67000
 temperature:           readable, output: 67000
 temperature:           readable, output: 35500
 temperature:           readable, output: 31000
 temperature:           not readable
 temperature:           readable, output: 32000
 temperature:           readable, output: 49000
 temperature:           not readable
 temperature:           readable, output: 40000
 temperature:           readable, output: 0
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      3

smc-fan:  Mt Sf type B

```

Here is the result of the scan-smc.sh script also

```

0: #KEY [4-ui32] 000000ff [....]
1: +LKS [1-flag] 07 [.]
2: ACID [8-ch8*] 0000000000000000 [........]
3: ALSC [16-{alc] 0192009608b00002000100640ed90000 [...........d....]
4: AUPO [1-ui8 ] 00 [.]
5: BATP [1-flag] 00 [.]
6: BISE [1-ui8 ]
7: BNum [1-ui8 ] 00 [.]
8: BRSC [2-ui16] 0000 [..]
9: CLK! [1-ui8 ] 00 [.]
10: CLKC [10-{clc] 00000e1000000e10198c [..........]
11: CLKH [8-{clh] 0000000000000000 [........]
12: CLKS [2-fp1f] 8000 [..]
13: CLKT [4-ui32] 00013e65 [..>e]
14: CONT [4-ui32] 16001600 [....]
15: CRCB [4-ui32] c512fc40 [...@]
16: CRCU [4-ui32]
17: Dlpc [1-flag]
18: EPCF [1-flag] 01 [.]
19: EPCI [4-ui32] 00800700 [....]
20: EPCV [2-ui16] 0001 [..]
21: EPMA [4-ch8*] 0000e080 [....]
22: EPMI [1-ui8 ] 00 [.]
23: EPUF [1-flag] 01 [.]
24: EPUI [4-ui32] 00800001 [....]
25: EPUV [2-ui16] 0001 [..]
26: EVCT [2-ui16] 0000 [..]
27: EVMD [4-ui32]
28: EVRD [32-ch8*] f6060300000124f0c101000001000f2b00000000000000000000000000000000 [......$........+................]
29: F0Ac [2-fpe2] 07cd [..]
30: F0ID [16-{fds] 010001004350555f4d454d2000000000 [....CPU_MEM ....]
31: F0Mn [2-fpe2] 07d0 [..]
32: F0Mt [2-ui16] 01f4 [..]
33: F0Mx [2-fpe2] 2d50 [-P]
34: F0Sf [2-fpe2] 12c0 [..]
35: F0Tg [2-fpe2] 07d0 [..]
36: F1Ac [2-fpe2] 07d1 [..]
37: F1ID [16-{fds] 01010400494f20000000000000000000 [....IO .........]
38: F1Mn [2-fpe2] 07d0 [..]
39: F1Mt [2-ui16] 0252 [.R]
40: F1Mx [2-fpe2] 2d50 [-P]
41: F1Sf [2-fpe2] 12c0 [..]
42: F1Tg [2-fpe2] 07d0 [..]
43: F2Ac [2-fpe2] 095a [.Z]
44: F2ID [16-{fds] 01000d00455848415553542000000000 [....EXHAUST ....]
45: F2Mn [2-fpe2] 07d0 [..]
46: F2Mt [2-ui16] 0258 [.X]
47: F2Mx [2-fpe2] 2d50 [-P]
48: F2Sf [2-fpe2] 12c0 [..]
49: F2Tg [2-fpe2] 0960 [.`]
50: F3Ac [2-fpe2] 0b3c [.<]
51: F3ID [16-{fds] 01021000505320202000000000000000 [....PS .......]
52: F3Mn [2-fpe2] 0b40 [.@]
53: F3Mt [2-ui16] 035c [.\]
54: F3Mx [2-fpe2] 2bc0 [+.]
55: F3Sf [2-fpe2] 12c0 [..]
56: F3Tg [2-fpe2] 0b40 [.@]
57: FNum [1-ui8 ] 04 [.]
58: FPhz [2-i16 ]
59: FS! [2-ui16] 0000 [..]
60: HDBS [1-ui8 ] 01 [.]
61: HDST [4-ui16] 00000000 [....]
62: HDSW [4-ui32] 00000000 [....]
63: ICAC [2-fp88] 088a [..]
64: ICAc [2-ui16] 1900 [..]
65: ICBC [2-fp88] 092f [./]
66: ICBc [2-ui16] 1b00 [..]
67: IM1s [2-ui16] 2e80 [..]
68: IM2s [2-ui16] 2680 [&.]
69: IMAS [2-fp88] 0269 [.i]
70: IMBS [2-fp88] 01f8 [..]
71: IN0C [2-fp88] 0db9 [..]
72: IN0c [2-ui16] 7d40 [}@]
73: Ie1S [2-fp88] 009e [..]
74: Ie1s [2-ui16] 0c40 [.@]
75: Ie2S [2-fp88] 0010 [..]
76: Ie2s [2-ui16] 0100 [..]
77: Ie3S [2-fp88] 000d [..]
78: Ie3s [2-ui16] 0100 [..]
79: Ie4S [2-fp88] 0006 [..]
80: Ie4s [2-ui16] 0080 [..]
81: IeAS [2-fp88] 000d [..]
82: IeAs [2-ui16] 0100 [..]
83: IeBS [2-fp88] 0009 [..]
84: IeBs [2-ui16] 00c0 [..]
85: Ip0C [2-fp88] 0d78 [.x]
86: Ip0c [2-ui16] 035e [.^]
87: Jp0D [2-ui16] 0000 [..]
88: Jp0S [2-ui16] 0000 [..]
89: Jp0W [2-ui16] 0000 [..]
90: JpFE [1-flag] 01 [.]
91: LAcN [1-ui8 ]
92: LAtN [2-ui16]
93: LS! [1-ui8 ] 00 [.]
94: LSCF [10-{lsc] 02ee0190800001020006 [..........]
95: LSDD [8-{lsd] 0002000300030019 [........]
96: LSDU [8-{lsd] 0003000200140003 [........]
97: LSFD [6-{lsf] 00000004001e [......]
98: LSFU [6-{lsf] 17700007003c [.p...<]
99: LSLB [2-{pwm] ffff [..]
100: LSLF [2-{pwm] 0000 [..]
101: LSLN [2-{pwm] 4e20 [N ]
102: LSOF [1-flag] 00 [.]
103: LSOO [1-flag]
104: LSPV [2-{pwm] 4e20 [N ]
105: LSRB [1-flag]
106: LSSB [2-{lso]
107: LSSE [1-flag] 01 [.]
108: LSSS [2-{lso]
109: LSSV [2-ui16] ffff [..]
110: LSUP [1-ui8 ]
111: MACA [4-ui32] 00000000 [....]
112: MACM [1-flag] 01 [.]
113: MACR [32-ch8*] 6368382a900124f0c101000001000f2b00000000000000000000000000000000 [ch8*..$........+................]
114: MDE [2-ui16] 00ff [..]
115: MDLC [2-ui16] 0000 [..]
116: MDSS [1-ui8 ] 02 [.]
117: MOCF [2-ui16] 0000 [..]
118: MSAL [1-si8 ]
119: MSDW [1-flag]
120: MSLD [1-ui8 ] 00 [.]
121: MSPS [1-{msp] 00 [.]
122: MSSD [1-si8 ] 03 [.]
123: MSSS [1-{mss] 00 [.]
124: MSTM [1-ui8 ] 00 [.]
125: MSWR [1-ui8 ]
126: NATJ [1-ui8 ] 00 [.]
127: NATi [2-ui16] 0000 [..]
128: NTOK [1-ui8 ]
129: NVPR [1-ui8 ] 00 [.]
130: NVPW [1-ui8 ]
131: ONMI [1-ui8 ] 00 [.]
132: OSK0 [32-ch8*] 6f757268617264776f726b62797468657365776f72647367756172646564706c [ourhardworkbythesewordsguardedpl]
133: OSK1 [32-ch8*] 65617365646f6e74737465616c2863294170706c65436f6d7075746572496e63 [easedontsteal(c)AppleComputerInc]
134: PCAC [2-fp88] 100d [..]
135: PCBC [2-fp88] 0e55 [.U]
136: PMAS [2-fp88] 1c97 [..]
137: PMBS [2-fp88] 173b [.;]
138: PN0C [2-fp88] 1454 [.T]
139: Pe1S [2-fp88] 077c [.|]
140: Pe2S [2-fp88] 009a [..]
141: Pe3S [2-fp88] 009a [..]
142: Pe4S [2-fp88] 0047 [.G]
143: PeAS [2-fp88] 009a [..]
144: PeBS [2-fp88] 0047 [.G]
145: PeTS [2-ui16] 0009 [..]
146: Pp0C [2-fpc4] 0a2b [.+]
147: RBr [8-ch8*] 6d34330000000000 [m43.....]
148: REV [6-{rev] 01070f000008 [......]
149: RMde [1-byte] 41 [A]
150: RPS0 [8-{psh] 0c02060408ce0000 [........]
151: RPlt [8-ch8*] 6d34330000000000 [m43.....]
152: RSvn [4-ui32] 00002721 [..'!]
153: RVBF [6-{rev] 01070f000008 [......]
154: RVUF [6-{rev] 01070f000008 [......]
155: SAS! [4-ui32]
156: SBF [2-ui16] 0000 [..]
157: SDRd [2-ui16]
158: SIS! [2-ui16]
159: SIT! [2-ui16]
160: SIU! [2-ui16]
161: SIV! [2-ui16]
162: SIW! [2-ui16]
163: SPC0 [1-ui8] 04 [.]
164: SPC1 [1-ui8] 01 [.]
165: SPC2 [1-ui8] 00 [.]
166: SPH0 [2-ui16] 0000 [..]
167: SPH1 [2-ui16] 0000 [..]
168: SPHS [1-ui8 ] 00 [.]
169: SPHT [1-ui8 ] 00 [.]
170: SPS! [2-ui16]
171: TA0P [2-sp78] 1c00 [..]
172: TC0C [2-sp78] 2f00 [/.]
173: TC0P [2-sp78] 2810 [(.]
174: TC1C [2-sp78] 0000 [..]
175: TC2C [2-sp78] 2f00 [/.]
176: TC3C [2-sp78] 0000 [..]
177: TCAH [2-sp78] 1f90 [..]
178: TCBH [2-sp78] 2090 [ .]
179: TH0P [2-sp78] 2320 [# ]
180: TH1P [2-sp78] 22e0 [".]
181: TH2P [2-sp78] 2220 [" ]
182: TH3P [2-sp78] 2080 [ .]
183: TM0P [2-sp78] 2900 [).]
184: TM0S [2-sp78] 4280 [B.]
185: TM1P [2-sp78] 2f00 [/.]
186: TM1S [2-sp78] 4500 [E.]
187: TM2P [2-sp78] 2f00 [/.]
188: TM2S [2-sp78] 4180 [A.]
189: TM3S [2-sp78] 3e00 [>.]
190: TM8P [2-sp78] 2800 [(.]
191: TM8S [2-sp78] 4300 [C.]
192: TM9P [2-sp78] 2f00 [/.]
193: TM9S [2-sp78] 4380 [C.]
194: TMAP [2-sp78] 3200 [2.]
195: TMAS [2-sp78] 3a00 [:.]
196: TMBS [2-sp78] 3a80 [:.]
197: TN0H [2-sp78] 4280 [B.]
198: TS0C [2-sp78] 2380 [#.]
199: Tp0C [2-sp78] 2f00 [/.]
200: Tp1C [2-sp78] 2b90 [+.]
201: Tv0S [2-sp78] 22b0 [".]
202: Tv1S [2-sp78] 2332 [#2]
203: VCAC [2-fp88] 013b [.;]
204: VCAc [2-ui16] 65c0 [e.]
205: VCBC [2-fp88] 013d [.=]
206: VCBc [2-ui16] 58c0 [X.]
207: VM0s [2-ui16] 02ac [..]
208: VM1s [2-ui16] 0198 [..]
209: VM2s [2-ui16] 02f4 [..]
210: VM3s [2-ui16] 0330 [.0]
211: VM4s [2-ui16] 02f8 [..]
212: VM8s [2-ui16] 02ac [..]
213: VM9s [2-ui16] 0198 [..]
214: VMAS [2-fp88] 0bdd [..]
215: VMAs [2-ui16] 02f4 [..]
216: VMBS [2-fp88] 0bcd [..]
217: VMBs [2-ui16] 0334 [.4]
218: VMCs [2-ui16] 02f4 [..]
219: VN0C [2-fp88] 017c [.|]
220: VS2c [2-ui16] 00c4 [..]
221: VS3c [2-ui16] 00bf [..]
222: VS4c [2-ui16] 00bd [..]
223: VS5c [2-ui16] 00bf [..]
224: VS6c [2-ui16] 00d3 [..]
225: VS7c [2-ui16] 00cb [..]
226: VS8c [2-ui16] 00bd [..]
227: VS9c [2-ui16] 00c4 [..]
228: VSAc [2-ui16] 0073 [.s]
229: VSBc [2-ui16] 00af [..]
230: VSCc [2-ui16] 00e9 [..]
231: VSDc [2-ui16] 00c9 [..]
232: VSEc [2-ui16] 00cb [..]
233: VSFc [2-ui16] 00bb [..]
234: VeES [2-fp88] 0be8 [..]
235: Vp0C [2-fp88] 0c12 [..]
236: Vp0c [2-ui16] 0c15 [..]
237: zDBG [1-ui8]
238: zSCI [1-ui8]
239: {clc [3-] 0001db [...]
240: {clf [3-] 0001e0 [...]
241: {clh [3-] 0001db [...]
242: {fds [3-] 0001db [...]
243: {lsc [3-] 0001dd [...]
244: {lsd [3-] 0001db [...]
245: {lsf [3-] 0001db [...]
246: {lsm [3-] 0001dd [...]
247: {lso [3-] 0001dd [...]
248: {lss [3-] 0001dd [...]
249: {msp [3-] 0001df [...]
250: {mss [3-] 0001df [...]
251: {psh [3-] 0001df [...]
252: {pwm [3-] 0001dc [...]
253: {rev [3-] 0001e0 [...]
254: {sds [3-] 0001db [...]

```

Any help anyone could offer would be greatly appreciated.

Still unanswered.

re-did the scan:

```

# dmidecode -s system-product-name

MacPro1,1

```

```


# ./applesmc-test.sh 
model: MacPro1,1

accelerometer: not present
fan:           present, readable, output: 500
light:         not present
leds:          not present
temperatures:  present,
 temperature:           not readable
 temperature:           readable, output: 48000
 temperature:           not readable
 temperature:           readable, output: 0
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 33750
 temperature:           readable, output: 33750
 temperature:           readable, output: 33000
 temperature:           readable, output: 31250
 temperature:           readable, output: 27000
 temperature:           readable, output: 50000
 temperature:           readable, output: 58000
 temperature:           readable, output: 58500
 temperature:           readable, output: 39000
 temperature:           readable, output: 65000
 temperature:           readable, output: 46000
 temperature:           readable, output: 68000
 temperature:           readable, output: 46000
 temperature:           readable, output: 64500
 temperature:           readable, output: 61000
 temperature:           not readable
 temperature:           readable, output: 39000
 temperature:           readable, output: 66500
 temperature:           readable, output: 46000
 temperature:           readable, output: 67000
 temperature:           readable, output: 65500
 temperature:           readable, output: 34000
 temperature:           readable, output: 29750
 temperature:           not readable
 temperature:           readable, output: 31500
 temperature:           readable, output: 49000
 temperature:           not readable
 temperature:           readable, output: 38500
 temperature:           readable, output: 0
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      3

smc-fan:  Mt Sf type B

```

any help on this would be very much appreciated.

---

### Post by coolbeet on 2011-07-29
Hi, I want get memory modules temperature, my machine is Apple Xserve with ubuntu 10.04, kernel  2.6.35-30-generic.

sudo dmidecode -s system-product-name

the system gave nothing, but if I use "sudo dmidecode",

```
# dmidecode 2.9
# No SMBIOS nor DMI entry point found, sorry.
```

./applesmc-test.sh
```
model: 
accelerometer: not present
fan:           not present
light:         not present
leds:          not present
temperatures:  not present
performance:    not performed

./applesmc-test.sh: line 128: cd: /sys/devices/platform/applesmc.768: No such file or directory
smc-fan: cat: key_count: No such file or directory
```

sudo ./scan-smc.sh
```
./scan-smc.sh: line 11: cd: /sys/devices/platform/applesmc.768/: No such file or directory
cat: key_count: No such file or directory
./scan-smc.sh: line 15: [: 0: unary operator expected
```

For "modprobe applesmc" && , 
```
FATAL: Error inserting applesmc (/lib/modules/2.6.35-30-generic/updates/dkms/applesmc.ko): No such device
```

Then for "dmesg | grep applesmc"
```
applesmc: supported laptop not found!
applesmc: driver init failed (ret=-19)!
```

Also, when I was installing the applesmc-dkms package, there are some kind of error message.

```
root@lake:/home/szhang# apt-get install applesmc-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  applesmc-dkms
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 10.5kB of archives.
After this operation, 41.0kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main applesmc-dkms all 0.17.3-maverick-mactel1 [10.5kB]
Fetched 10.5kB in 0s (30.2kB/s)        
Selecting previously deselected package applesmc-dkms.
(Reading database ... 46576 files and directories currently installed.)
Unpacking applesmc-dkms (from .../applesmc-dkms_0.17.3-maverick-mactel1_all.deb) ...
Setting up applesmc-dkms (0.17.3-maverick-mactel1) ...
Loading new applesmc-0.17.3 DKMS files...

Loading tarball for module: applesmc / version: 0.17.3

Loading /usr/src/applesmc-0.17.3...
Creating /var/lib/dkms/applesmc/0.17.3/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

**[COLOR="Red"]Kernel preparation unnecessary for this kernel.  Skipping...[/COLOR]**

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-30-generic -C /lib/modules/2.6.35-30-generic/build SUBDIRS=/var/lib/dkms/applesmc/0.17.3/build modules....
cleaning build area....

DKMS: build Completed.
Installing module...

applesmc.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/2.6.35-30-generic/updates/dkms/

depmod......

DKMS: install Completed.
```

Thank you so much~~~

---

### Post by metatechbe on 2011-07-29
> **coolbeet said:**
> Hi, I want get memory modules temperature, my machine is Apple Xserve with ubuntu 10.04, kernel  2.6.35-30-generic.

```
# dmidecode 2.9
# No SMBIOS nor DMI entry point found, sorry.
```


Hello,

Xserve machines do not have a BIOS compatibility layer.
Your machine must be be booted in EFI mode, hence the error.
You could try "fakebios" in grub.cfg if you are lucky.

---

### Post by coolbeet on 2011-07-29
> **metatechbe said:**
> Hello,

Xserve machines do not have a BIOS compatibility layer.
Your machine must be be booted in EFI mode, hence the error.
You could try "fakebios" in grub.cfg if you are lucky.

Hi, thanks for the information.

The machine does booted in EFI mode, and there are already "fakebios" in grub.cfg
```
.......
menuentry "Ubuntu System" {
   fakebios
   root=(hd0,8)
   linux /vmlinuz root=/dev/sda8 ro vga=normal video=efifb
   initrd /initrd.img
}
.......
```

Is there any other way to fix that? I really hate this Xserve:-(

Thank you so much~

---

### Post by dfacto on 2011-08-03
Ran the scan on the new 2011 MacBookAir4,2.

Please let me know what else is needed to get this fully supported!

---

### Post by alexmurray on 2011-08-03
Looks like it is already working from your output - what is in the directory /sys/devices/platform/applesmc.768/

---

### Post by dfacto on 2011-08-03
> **alexmurray said:**
> Looks like it is already working from your output - what is in the directory /sys/devices/platform/applesmc.768/

Hey thanks for getting back to me!

It may indeed be working.  I am concerned that there was some issue since the fans seem to run all the time after installing macfantld.  Prior to installing macfantld I felt like it ran a tad hot at times.  Obviously these are subjective statements but still I want to be sure there are no troubles down the line (some scary posts about the dangers of running non-osx on the new MBA). 

Cheers

---

### Post by alexmurray on 2011-08-04
Yep all the sensors are listed there so looks good for the new MB(A) models.

---

### Post by dfacto on 2011-08-04
> **alexmurray said:**
> Yep all the sensors are listed there so looks good for the new MB(A) models.

Good; thanks for confirming.  This is my first mac so I was wondering if you knew if it is normal for macfanctld to run the fans all the time?

---

### Post by alexmurray on 2011-08-04
No idea, I don't use macfanctld on my MBP5,1 - it seems cool enough without it. Perhaps you could try resetting the SMC to see if that helps with cooling issues?

---

### Post by adamski99 on 2012-07-08
Hi,

on a Macbook pro 9,2 here, with my moded applesmc as per my post in:

[http://ubuntuforums.org/showthread.php?t=2006289&page=3](http://ubuntuforums.org/showthread.php?t=2006289&page=3)

cheers

adam


applesmc-test: completes with 3 read arg fails in the syslog

```

accelerometer: present, readable, output: (-6,0,262)
fan:           present, readable, output: 2000
light:         present, readable, output: (1,0)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           readable, output: 55000
 temperature:           readable, output: 0
 temperature:           readable, output: 55000
 temperature:           readable, output: 56000
 temperature:           readable, output: 255750
 temperature:           readable, output: 55500
 temperature:           readable, output: 57000
 temperature:           readable, output: 39000
 temperature:           readable, output: 48250
 temperature:           readable, output: 66000
 temperature:           readable, output: 41250
 temperature:           readable, output: 43000
 temperature:           readable, output: 29500
 temperature:           readable, output: 37750
 temperature:           readable, output: 34250
 temperature:           readable, output: 34250
 temperature:           readable, output: 31250
 temperature:           readable, output: 56250
 temperature:           readable, output: 57000
 temperature:           readable, output: 500
 temperature:           readable, output: 48250
 temperature:           readable, output: 55000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      166

smc-fan:  Mt type C

```


scan-smc: 

```

0: #KEY [4-ui32] 00000177 [...w]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 01 [.]
4: ACCL [1-ui8 ] 01 [.]
5: ACEN [1-ui8 ] 01 [.]
6: ACFP [1-flag] 01 [.]
7: ACIC [2-ui16] 0d80 [..]
8: ACID [8-ch8*] baa56dcac00310fb [..m.....]
9: ACIN [1-flag] 01 [.]
10: ACLM [2-ui16] 0d80 [..]
11: AL! [2-ui16] 0000 [..]
12: ALI0 [4-{ali] 04000f00 [....]
13: ALI1 [4-{ali] 00000000 [....]
14: ALP0 [4-{alp] 13330780 [.3..]
15: ALP1 [4-{alp] 00000000 [....]
16: ALRV [2-ui16] 0001 [..]
17: ALSC [16-{alc] 00c8009603e8000f0001015e1d030106 [...........^....]
18: ALSF [2-fp1f] 1d2f [./]
19: ALSL [2-ui16] 0014 [..]
20: ALV0 [10-{alv] 0101010f00a10005195a [.........Z]
21: ALV1 [10-{alv] 00010000000000000000 [..........]
22: AUPO [1-ui8 ] 00 [.]
23: B0AC [2-si16] 0ade [..]
24: B0AV [2-ui16] 2f21 [/!]
25: B0Al [2-ui16] ffff [..]
26: B0Am [1-ui8 ] 10 [.]
27: B0Ar [1-ui8 ] 00 [.]
28: B0As [1-ui8 ] 00 [.]
29: B0At [2-ui16] 0960 [.`]
30: B0Au [2-ui16] 0960 [.`]
31: B0BI [1-hex_] 51 [Q]
32: B0CT [2-ui16] 0006 [..]
33: B0FC [2-ui16] 1662 [.b]
34: B0LI [2-ui16] 0f80 [..]
35: B0RI [2-ui16] 0fa0 [..]
36: B0RM [2-ui16] 0c44 [.D]
37: B0St [2-hex_] 0080 [..]
38: B0TF [2-ui16] 007c [.|]
39: BALG [1-ui8 ] 00 [.]
40: BATP [1-flag] 00 [.]
41: BBAD [1-flag] 00 [.]
42: BBIN [1-flag] 01 [.]
43: BC1V [2-ui16] 0fc0 [..]
44: BC2V [2-ui16] 0fa9 [..]
45: BC3V [2-ui16] 0fb8 [..]
46: BCHA [1-ui8 ] 02 [.]
47: BCHB [1-ui8 ] 06 [.]
48: BCHF [1-ui8 ]
49: BCHG [1-ui8 ]
50: BCHL [1-ui8 ]
51: BCHO [1-ui8 ] 1f [.]
52: BCHP [1-ui8 ] 07 [.]
53: BCHR [1-ui8 ] 3a [:]
54: BCHT [1-ui8 ] 06 [.]
55: BCHX [1-ui8 ] 01 [.]
56: BCLM [1-ui8 ] 64 [d]
57: BCMV [2-ui16] 0fc0 [..]
58: BEMB [1-flag] 01 [.]
59: BFCT [2-ui16] 0000 [..]
60: BFLO [1-ui8 ] 00 [.]
61: BILB [1-ui8 ] 1f [.]
62: BILO [2-ui8 ] 1f07 [..]
63: BLPT [20-ch8*] 0101041a10e72f70000000000000000000000000 [....../p............]
64: BNCM [1-ui8 ]
65: BNCR [1-ui8 ] 00 [.]
66: BNum [1-ui8 ] 01 [.]
67: BPII [2-sp78] fd48 [.H]
68: BPIT [2-sp78] 0600 [..]
69: BRII [2-sp78] 0001 [..]
70: BRIT [2-sp78] 0360 [.`]
71: BRLP [2-ui16] 0039 [.9]
72: BROS [2-ui16] 0096 [..]
73: BRS0 [2-ui16] 0032 [.2]
74: BRSC [2-ui16] 0037 [.7]
75: BRWK [2-ui16] 0096 [..]
76: BSAC [1-hex_] 33 [3]
77: BSIn [1-hex_] 43 [C]
78: BTIL [2-ui16] 0b00 [..]
79: BTTI [1-ui8 ] 02 [.]
80: BTVI [1-ui8 ] 01 [.]
81: BTVR [1-ui8 ] 01 [.]
82: BTVT [1-ui8 ] 01 [.]
83: BWLM [1-ui8 ] 00 [.]
84: CHBI [2-ui16] 0b00 [..]
85: CHBV [2-ui16] 3130 [10]
86: CHGC [2-ui16] 0062 [.b]
87: CHGD [1-flag]
88: CHGI [2-ui16] 0b00 [..]
89: CHGV [2-ui16] 3130 [10]
90: CHII [2-ui16] 0d80 [..]
91: CHLC [1-ui8 ] 01 [.]
92: CLK! [1-ui8 ] 00 [.]
93: CLKC [10-{clc] 00000e1000000e10198c [..........]
94: CLKH [8-{clh] 0000708000011940 [..p....@]
95: CLKS [2-fp1f] 8000 [..]
96: CLKT [4-ui32] 00009ea2 [....]
97: CLSD [2-ui16] 0a18 [..]
98: CLWK [2-ui16] 0047 [.G]
99: CRCF [4-ui32]
100: DPLM [5-{lim]
101: ECIP [19-ch8*]
102: ECIT [1-ui8 ]
103: EECC [4-ui32]
104: ENV0 [1-ui8 ] 03 [.]
105: EPCA [4-ui32] 00006000 [..`.]
106: EPCF [1-flag] 01 [.]
107: EPCI [4-ui32] 06600700 [.`..]
108: EPCV [2-ui16] 0001 [..]
109: EPMA [4-ch8*] 00005810 [..X.]
110: EPMI [1-ui8 ] 00 [.]
111: EPUA [4-ui32] 00005800 [..X.]
112: EPUF [1-flag] 01 [.]
113: EPUI [4-ui32] 06600001 [.`..]
114: EPUV [2-ui16] 0001 [..]
115: EVCT [2-ui16] 0f0f [..]
116: EVHF [28-ch8*] 00000000000000000000000000000000000000000000000000000000 [............................]
117: EVMD [4-ui32]
118: EVRD [32-ch8*] f6060300004099d07105160028012fd1d1083081ffc09db861108840ff8136d1 [.....@..q...(./...0.....a..@..6.]
119: EVSL [1-ui8 ] 00 [.]
120: F0Ac [2-fpe2] 1f34 [.4]
121: F0ID [16-{fds] 00000a00457868617573742020000000 [....Exhaust ...]
122: F0Mn [2-fpe2] 1f40 [.@]
123: F0Mt [2-ui16] 0000 [..]
124: F0Mx [2-fpe2] 60e0 [`.]
125: F0Tg [2-fpe2] 1f40 [.@]
126: FNum [1-ui8 ] 01 [.]
127: FPDc [2-fp79] 319c [1.]
128: FRmn [2-ui16] 0000 [..]
129: FRmp [2-ui16] 0000 [..]
130: FS! [2-ui16] 0000 [..]
131: FSDc [1-ui8] 00 [.]
132: G3AO [4-ui32] 00000000 [....]
133: G3WD [1-flag] 00 [.]
134: HBKP [32-ch8*] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
135: HBKT [4-ui32] 00054600 [..F.]
136: HDBS [1-ui8 ] 01 [.]
137: HDST [4-hex_] 00000000 [....]
138: HDSW [4-hex_] 004b004b [.K.K]
139: IC0C [2-sp78] 06d6 [..]
140: IC0R [2-sp5a] 02d8 [..]
141: IC1C [2-sp5a] 022d [.-]
142: ID0R [2-sp5a] 0c2f [./]
143: IHDC [2-sp5a] 004d [.M]
144: IM0C [2-sp5a] 00e9 [..]
145: IN0C [2-sp5a] 029d [..]
146: IO0R [2-sp5a] 01ce [..]
147: IPBR [2-sp5a] 0096 [..]
148: LAcN [1-ui8 ]
149: LAtN [2-ui16]
150: LC2D [2-ui16] 8796 [..]
151: LC2E [2-ui16] 8796 [..]
152: LCCC [1-ui8 ] 00 [.]
153: LCCN [1-ui8 ] 7d [}]
154: LCCQ [1-ui8 ] 53 [S]
155: LCKA [1-ui8 ] 36 [6]
156: LCKN [1-ui8 ] a0 [.]
157: LCLD [2-ui16] 0000 [..]
158: LCLG [1-ui8 ] 00 [.]
159: LCSA [1-ui8 ] c3 [.]
160: LCTN [1-ui8 ] 5c [\]
161: LCTQ [1-ui8 ] 26 [&]
162: LDEN [2-ui16] 0000 [..]
163: LDI2 [1-ui8 ] 01 [.]
164: LDKN [1-ui8 ] 02 [.]
165: LDLG [1-ui8 ]
166: LDS4 [1-ui8 ] 00 [.]
167: LDSP [1-flag]
168: LDT1 [1-ui8 ] 00 [.]
169: LDT2 [2-ui16] 0000 [..]
170: LDT4 [4-ui32] 00000000 [....]
171: LDTF [2-ui16] 0000 [..]
172: LDWE [4-ui32] 00000000 [....]
173: LKSB [2-{lkb]
174: LS! [1-ui8 ] 00 [.]
175: LSCF [10-{lsc] c8009001008002020020 [......... ]
176: LSDD [8-{lsd] 0200030003001900 [........]
177: LSDU [8-{lsd] 0300020014000300 [........]
178: LSFD [6-{lsf] 000004008c00 [......]
179: LSFU [6-{lsf] 000004008c00 [......]
180: LSLB [2-{pwm] ffff [..]
181: LSLF [2-{pwm] 0000 [..]
182: LSLN [2-{pwm] ffff [..]
183: LSOF [1-flag] 01 [.]
184: LSOO [1-flag]
185: LSPV [2-{pwm] 0000 [..]
186: LSRB [1-flag]
187: LSSB [2-{lso]
188: LSSE [1-flag] 01 [.]
189: LSSS [2-{lso]
190: LSSV [2-ui16] ffff [..]
191: LSUP [1-ui8 ]
192: MACA [4-ui32] 00000000 [....]
193: MACM [1-flag] 01 [.]
194: MACR [32-ch8*]
195: MOCF [2-ui16] 8300 [..]
196: MOCN [2-ui16] e000 [..]
197: MOHD [1-ui8 ] 0a [.]
198: MOHT [2-sp78] 01e0 [..]
199: MOIC [2-ui16] 0000 [..]
200: MOLD [1-ui8 ] 0a [.]
201: MOLT [2-sp78] 0020 [. ]
202: MOST [2-ui16] 8000 [..]
203: MOTP [1-ui8 ] 01 [.]
204: MO_X [2-sp78] fff5 [..]
205: MO_Y [2-sp78] 000a [..]
206: MO_Z [2-sp78] 0107 [..]
207: MSAL [1-hex_] 4b [K]
208: MSAc [2-fp88] 0000 [..]
209: MSAf [2-fp6a] 0000 [..]
210: MSAg [2-fp88] 0000 [..]
211: MSAm [2-fp88] 0000 [..]
212: MSDI [1-flag] 00 [.]
213: MSDW [1-flag]
214: MSG3 [1-flag] 00 [.]
215: MSLB [2-ui16] 0000 [..]
216: MSLC [1-ui8 ] 00 [.]
217: MSLD [1-ui8 ] 00 [.]
218: MSLF [1-ui8 ] 00 [.]
219: MSLG [1-ui8 ] 00 [.]
220: MSLP [1-ui8 ] 13 [.]
221: MSLS [1-ui8 ] 04 [.]
222: MSLT [2-fp88] 1d00 [..]
223: MSPA [2-fp6a] 0000 [..]
224: MSPB [1-flag] 00 [.]
225: MSPC [1-ui8 ] 0e [.]
226: MSPI [1-ui8 ] 00 [.]
227: MSPM [1-ui8 ] 04 [.]
228: MSPS [2-ui16] 0003 [..]
229: MSPT [5-ui8 ]
230: MSQA [1-flag] 00 [.]
231: MSQC [1-ui8 ] 00 [.]
232: MSQD [1-si8 ] 00 [.]
233: MSQF [1-flag] 00 [.]
234: MSQL [1-ui8 ] 00 [.]
235: MSSD [1-si8 ] 03 [.]
236: MSSF [4-ui32] 00000000 [....]
237: MSSG [4-ui32] 00000000 [....]
238: MSSP [1-si8 ] 05 [.]
239: MSSR [1-flag] 01 [.]
240: MSSS [1-{mss] 00 [.]
241: MSTC [2-ui16] 0000 [..]
242: MSTS [1-ui8 ] 06 [.]
243: MSTc [1-ui8 ] 00 [.]
244: MSTe [1-ui8 ] 00 [.]
245: MSTf [1-ui8 ] 00 [.]
246: MSTi [1-ui8 ] 00 [.]
247: MSTm [1-ui8 ] 00 [.]
248: MSWA [2-fp6a] 0000 [..]
249: MSWE [1-ui8] 00 [.]
250: MSWF [2-ui16] 03e8 [..]
251: MSWO [2-ui16] 03e8 [..]
252: MSWP [1-ui8] 00 [.]
253: MSWr [1-ui8 ] 00 [.]
254: MSXC [4-ch8*] 00000000 [....]
255: MSXD [16-ch8*] 00000000000000000000000000000000 [................]
256: MSXK [32-ch8*] f3f4000000000000000000000000000000000000000000000000000000000000 [................................]
257: MSXN [1-ui8 ] 22 ["]
258: MSXS [4-ch8*] 01020304 [....]
259: MSXb [1-ui8 ] 00 [.]
260: MSXc [4-ch8*] 00000000 [....]
261: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
262: MSXk [32-ch8*] 0102030405060708090a0b0c0d0e0f101112131415161718dcdddef0f1f2f400 [................................]
263: MSXm [2-ui16] 0008 [..]
264: MSXn [1-ui8 ] 1f [.]
265: MSXs [4-ui32] 01020304 [....]
266: MSa! [1-hex_] 00 [.]
267: MSac [1-ui8 ] 00 [.]
268: MSaf [1-ui8 ] 00 [.]
269: MSag [1-ui8 ] 00 [.]
270: MSam [1-ui8 ] 00 [.]
271: MSap [1-ui8 ] 00 [.]
272: MSci [1-ui8]
273: MScr [2-hex_]
274: MSii [1-ui8]
275: MSir [2-hex_]
276: MVDS [1-flag] 00 [.]
277: MVS4 [1-ui8 ] 00 [.]
278: NACK [1-ui8 ]
279: NATJ [1-ui8 ] 00 [.]
280: NATi [2-ui16] 0000 [..]
281: NOPB [1-ui8 ] 00 [.]
282: NTOK [1-ui8 ]
283: ONMI [1-ui8 ] 00 [.]
284: PC0C [2-sp78] 05ae [..]
285: PC0R [2-sp78] 08a4 [..]
286: PC1C [2-sp78] 0090 [..]
287: PC2C [2-sp78] 0000 [..]
288: PCPC [2-sp78] 02e0 [..]
289: PCPG [2-sp78] 000c [..]
290: PCPT [2-sp78] 0551 [.Q]
291: PDTR [2-sp78] 3232 [22]
292: PHDC [2-sp78] 003c [.<]
293: PHPC [2-sp78] 08a4 [..]
294: PM0C [2-sp78] 0056 [.V]
295: PN0C [2-sp78] 0002 [..]
296: PO0R [2-sp78] 0579 [.y]
297: PPBR [2-sp78] 01c9 [..]
298: PSTR [2-sp78] 10b3 [..]
299: PTHC [2-sp78] 2d00 [-.]
300: RBr [8-ch8*] 6272616e63680000 [branch..]
301: REV [6-{rev] 02020f000038 [.....8]
302: RMde [1-char] 41 [A]
303: RPlt [8-ch8*] 6a33300000000000 [j30.....]
304: RSvn [4-ui32] 00000000 [....]
305: RVBF [6-{rev] 02020f000038 [.....8]
306: RVCR [6-{rev] ffffffffffff [......]
307: RVUF [6-{rev] 02020f000038 [.....8]
308: SAS! [4-hex_] 00ffffff [....]
309: SBF [4-hex_] 00000000 [....]
310: SBFC [1-flag]
311: SBFD [4-hex_] 00000000 [....]
312: SBFE [1-flag] 01 [.]
313: SBFL [4-hex_] 00000000 [....]
314: SBFN [4-hex_] 00000000 [....]
315: SBFU [4-hex_] 00000000 [....]
316: SBFV [4-hex_] 0000001f [....]
317: SBS! [2-ui16]
318: SCIA [2-ui16] 03f8 [..]
319: SCII [1-ui8 ] 03 [.]
320: SCIL [1-ui8 ] 00 [.]
321: SCXC [2-sp78] 6900 [i.]
322: SFBR [1-ui8 ] 04 [.]
323: SIS! [4-hex_]
324: SMBC [6-ch8*]
325: SMBG [1-ui8 ]
326: SMBR [32-ch8*]
327: SMBS [2-ch8*]
328: SMBW [32-ch8*]
329: SPDO [1-ui8 ] 01 [.]
330: SPH0 [2-ui16] 0000 [..]
331: SPHR [4-ui32] 00000000 [....]
332: SPHS [1-ui8 ] 00 [.]
333: SPHT [2-ui16] 0000 [..]
334: SPHZ [1-ui8]
335: SPT! [1-hex_]
336: SPU! [4-hex_] 00000000 [....]
337: SRS! [4-hex_]
338: SWER [1-hex_] 00 [.]
339: TA0P [2-sp78] 29a0 [).]
340: TB0T [2-sp78] 2319 [#.]
341: TB1T [2-sp78] 2319 [#.]
342: TB2T [2-sp78] 2033 [ 3]
343: TC0E [2-sp78] 386d [8m]
344: TC0F [2-sp78] 395c [9\]
345: TC0J [2-sp78] 00ef [..]
346: TC0P [2-sp78] 30c0 [0.]
347: TC1C [2-sp78] 3600 [6.]
348: TC2C [2-sp78] 3700 [7.]
349: TCFC [2-ui16] 001e [..]
350: TCGC [2-sp78] 3900 [9.]
351: TCSA [2-sp78] 3b00 [;.]
352: TCTD [2-sp78] 001d [..]
353: TCXC [2-sp78] 3a18 [:.]
354: TG1D [2-sp78] 395c [9\]
355: TM0P [2-sp78] 2740 ['@]
356: TM0S [2-sp78] 309e [0.]
357: TPCD [2-sp78] 4200 [B.]
358: Th1H [2-sp78] 2b40 [+@]
359: Ts0P [2-sp78] 1e40 [.@]
360: Ts0S [2-sp78] 25e0 [%.]
361: UPRC [2-ui16] 0001 [..]
362: VC0C [2-sp5a] 035e [.^]
363: VD0R [2-sp5a] 41fe [A.]
364: VN0C [2-sp5a] 001e [..]
365: VP0R [2-sp5a] 30b0 [0.]
366: WCPD [1-ui8 ] 00 [.]
367: WCPW [1-ui8 ] 01 [.]
368: WKEN [1-ui8 ] 00 [.]
369: WKTP [1-ui8 ] 00 [.]
370: WOr0 [1-si8 ] ff [.]
371: WOw0 [1-si8 ] ff [.]
372: zDBG [1-ui8] 00 [.]
373: zDSF [1-flag] 00 [.]
374: zRST [1-ui8]


```

---

### Post by kosumi68 on 2012-07-08
Hi adamski,

> **adamski99 said:**
> 
```

 reads per second:      166

```


This is considerably faster than previous models, roughly four times as fast. Nicely consistent with the need for a smaller
minimum wait time.

Thanks!

---

