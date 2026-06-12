---
title: "New applesmc module for all models - Call for testing"
date: 2010-10-27
forum: Apple Hardware Users
---

### Post by kosumi68 on 2010-10-27
New applesmc kernel module with dynamic configuration

The amount of machines supported by this module has increased
rapidly over the past years, and the detailed driver support
of the many flavors is quickly becoming a problem.

The attached dkms package contains a new, dynamically
configured driver which fixes a number of outstanding
issues:

* Support for all new models since MacbookPro 6.
* Support for variable number of processors in the MacPros.
* Handles the odd temperature sensor types found on new models.
* Fixes minor read problems on many intermediate models.

And, of course, all models back to the MacBook1,1 should work at least as well as before. :-)

Please test and report the outcome in this thread, stating your machine model and a simple "OK" or a description of the problem. As soon as things seem to work as expected, the patches will go upstream.

Thanks!

---

### Post by Niels den Otter on 2010-10-28
FWIW. Loads fine on my Macbook 5,1.

Output previous (default 10.10 driver):

Oct 28 09:24:42 sambal kernel: [   25.518617] applesmc: Apple MacBook 5 detected:
Oct 28 09:24:42 sambal kernel: [   25.518620] applesmc:  - Model with accelerometer
Oct 28 09:24:42 sambal kernel: [   25.518622] applesmc:  - Model with light sensors and backlight
Oct 28 09:24:42 sambal kernel: [   25.518625] applesmc:  - Model with 14 temperature sensors
Oct 28 09:24:42 sambal kernel: [   25.583889] applesmc: device successfully initialized (0xe0, 0x00).
Oct 28 09:24:42 sambal kernel: [   25.583891] applesmc: device successfully initialized.
Oct 28 09:24:42 sambal kernel: [   25.586382] applesmc: 1 fans found.
Oct 28 09:24:42 sambal kernel: [   25.646181] input: applesmc as /devices/platform/applesmc.768/input/input12
Oct 28 09:24:42 sambal kernel: [   25.947014] Registered led device: smc::kbd_backlight
Oct 28 09:24:42 sambal kernel: [   25.947037] applesmc: driver successfully loaded.


Output of your driver when loading;

Oct 28 20:43:04 sambal kernel: [27112.310389] applesmc: Apple MacBook detected
Oct 28 20:43:05 sambal kernel: [27112.483226] applesmc: key=271 fan=1 temp=14 acc=1, light=2, keyb=1
Oct 28 20:43:05 sambal kernel: [27112.527493] input: applesmc as /devices/platform/applesmc.768/input/input18
Oct 28 20:43:05 sambal kernel: [27112.527670] Registered led device: smc::kbd_backlight
Oct 28 20:43:05 sambal kernel: [27112.527693] applesmc: driver successfully loaded.


Both the new and original driver shows this output;

Oct 28 20:44:34 sambal kernel: [27201.814535] applesmc: wait status failed: 4 != 10
Oct 28 20:45:19 sambal kernel: [27247.138975] applesmc: wait status failed: 4 != 10

Don't know what this means.


-- Niels

---

### Post by linuxopjemac on 2010-10-28
MacBook 2,1 here.

Before installation:
jeroen@jeroen-mint ~ $ dmesg | grep smc
[   12.979070] applesmc: Apple MacBook (v2) detected:
[   12.979074] applesmc:  - Model with accelerometer
[   12.979076] applesmc:  - Model without light sensors and backlight
[   12.979078] applesmc:  - Model with 10 temperature sensors
[   12.979734] applesmc: device has already been initialized (0xe0, 0x00).
[   12.979736] applesmc: device successfully initialized.
[   12.980533] applesmc: 1 fans found.
[   12.984063] input: applesmc as /devices/platform/applesmc.768/input/input9
[   12.984432] applesmc: driver successfully loaded.
jeroen@jeroen-mint ~ $ dpkg -l | grep smc
rc  applesmc-dkms                         0.17.0~rc1                                      Supplementary applesmc support
jeroen@jeroen-mint ~ $ 




Installed without problems.
jeroen@jeroen-mint ~ $ dmesg | grep smc
[   13.915411] applesmc: Apple MacBook detected
[   14.104336] applesmc: key=225 fan=1 temp=10 acc=1, light=0, keyb=0
[   14.183051] input: applesmc as /devices/platform/applesmc.768/input/input11
[   14.183867] applesmc: driver successfully loaded.
jeroen@jeroen-mint ~ $ 


The line [   14.104336] applesmc: key=225 fan=1 temp=10 acc=1, light=0, keyb=0 I didn't have before. What it used to detect was MacBook v2. Now that info seems to be lost.

---

### Post by linuxopjemac on 2010-10-28
The problem I experience now is that the screen dims by itself

update: happens with old module too...

---

### Post by kosumi68 on 2010-10-28
> **linuxopjemac said:**
> MacBook 2,1 here.

The line [   14.104336] applesmc: key=225 fan=1 temp=10 acc=1, light=0, keyb=0 I didn't have before. What it used to detect was MacBook v2. Now that info seems to be lost.

Thanks for testing! The new driver only contains generic model matching, and your 2.1 is still a MacBook. :-) All special details of your particular 2.1 model are instead read dynamically via the SMC itself.

@Niels: Thanks, I will return with another package that hopefully will contain more informative error messages.

Cheers!

---

### Post by kosumi68 on 2010-10-29
New version of the dkms package, with more informative warnings. Occasional read errors is not a problem, but a consistent read failure most likely is due to a misinterpretation of some data type. Knowing about such errors would be very helpful.

Thanks!

---

### Post by linuxopjemac on 2010-10-29
sudo dpkg -i applesmc-dkms_0.17.0~rc2_all.deb 
[sudo] password for jeroen: 
Selecting previously deselected package applesmc-dkms.
(Reading database ... 118252 files and directories currently installed.)
Unpacking applesmc-dkms (from applesmc-dkms_0.17.0~rc2_all.deb) ...
Setting up applesmc-dkms (0.17.0~rc2) ...
Loading new applesmc-0.17.0 DKMS files...

Loading tarball for module: applesmc / version: 0.17.0

Loading /usr/src/applesmc-0.17.0...
Creating /var/lib/dkms/applesmc/0.17.0/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-21-generic -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/var/lib/dkms/applesmc/0.17.0/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-21-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/applesmc/0.17.0/build/ for more information.
0
0
dpkg: error processing applesmc-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 applesmc-dkms


cat /var/lib/dkms/applesmc/0.17.0/build/make.log 
DKMS make.log for applesmc-0.17.0 for kernel 2.6.32-21-generic (i686)
Fri Oct 29 16:10:07 CEST 2010
make: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /var/lib/dkms/applesmc/0.17.0/build/applesmc.o
/var/lib/dkms/applesmc/0.17.0/build/applesmc.c: In function ‘read_smc’:
/var/lib/dkms/applesmc/0.17.0/build/applesmc.c:218: error: implicit declaration of function ‘pr_warn’
make[1]: *** [/var/lib/dkms/applesmc/0.17.0/build/applesmc.o] Error 1
make: *** [_module_/var/lib/dkms/applesmc/0.17.0/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'

---

### Post by kosumi68 on 2010-10-29
> **linuxopjemac said:**
> sudo dpkg -i applesmc-dkms_0.17.0~rc2_all.deb 


Right, pr_info and co are quite new... code defines them if not defined now, and the package in the previous post has been updated. Thanks!

---

### Post by ryanczak on 2010-10-29
Installed. Will report any problems. Does this new version of applesmc provide better fan control than the old version? I am currently using macfanctld from the mactel ppa. Is it still required? 

Before:
```
Oct 29 10:52:10 fruit kernel: [    9.228369] applesmc: Apple MacBook Pro 7 detected:
Oct 29 10:52:10 fruit kernel: [    9.228373] applesmc:  - Model with accelerometer
Oct 29 10:52:10 fruit kernel: [    9.228375] applesmc:  - Model with light sensors and backlight
Oct 29 10:52:10 fruit kernel: [    9.228377] applesmc:  - Model with 15 temperature sensors
Oct 29 10:52:10 fruit kernel: [    9.293549] applesmc: device successfully initialized (0xe0, 0x00).
Oct 29 10:52:10 fruit kernel: [    9.293552] applesmc: device successfully initialized.
Oct 29 10:52:10 fruit kernel: [    9.294484] applesmc: 1 fans found.
Oct 29 10:52:10 fruit kernel: [    9.311559] applesmc: driver successfully loaded.
Oct 29 10:52:15 fruit kernel: [   15.155481] applesmc: light sensor data length set to 10
Oct 29 10:53:59 fruit kernel: [  121.544600] applesmc: wait status failed: 5 != 1

```


After:
```
Oct 29 10:53:59 fruit kernel: [  121.544600] applesmc: wait status failed: 5 != 1
Oct 29 10:57:00 fruit kernel: [    9.121210] applesmc: Apple MacBook Pro detected
Oct 29 10:57:00 fruit kernel: [    9.741466] applesmc: key=321 fan=1 temp=15 acc=1, light=2, keyb=1
Oct 29 10:57:00 fruit kernel: [    9.802587] input: applesmc as /devices/platform/applesmc.768/input/input10
Oct 29 10:57:00 fruit kernel: [    9.803298] applesmc: driver successfully loaded
Oct 29 10:57:06 fruit kernel: [   15.920292] applesmc: light sensor data length set to 10
```

---

### Post by linuxopjemac on 2010-10-29
can't install still:

jeroen@jeroen-mint ~/Downloads $ sudo dpkg -i applesmc-dkms_0.17.0~rc2_all.deb 
Selecting previously deselected package applesmc-dkms.
(Reading database ... 118252 files and directories currently installed.)
Unpacking applesmc-dkms (from applesmc-dkms_0.17.0~rc2_all.deb) ...
Setting up applesmc-dkms (0.17.0~rc2) ...
Loading new applesmc-0.17.0 DKMS files...

Loading tarball for module: applesmc / version: 0.17.0

Loading /usr/src/applesmc-0.17.0...
Creating /var/lib/dkms/applesmc/0.17.0/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-21-generic -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/var/lib/dkms/applesmc/0.17.0/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-21-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/applesmc/0.17.0/build/ for more information.
0
0
dpkg: error processing applesmc-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 applesmc-dkms


jeroen@jeroen-mint ~/Downloads $ cat /var/lib/dkms/applesmc/0.17.0/build/make.log 
DKMS make.log for applesmc-0.17.0 for kernel 2.6.32-21-generic (i686)
Fri Oct 29 17:48:42 CEST 2010
make: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /var/lib/dkms/applesmc/0.17.0/build/applesmc.o
/var/lib/dkms/applesmc/0.17.0/build/applesmc.c: In function ‘read_smc’:
/var/lib/dkms/applesmc/0.17.0/build/applesmc.c:227: error: implicit declaration of function ‘pr_warn’
make[1]: *** [/var/lib/dkms/applesmc/0.17.0/build/applesmc.o] Error 1
make: *** [_module_/var/lib/dkms/applesmc/0.17.0/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
jeroen@jeroen-mint ~/Downloads $

---

### Post by kosumi68 on 2010-10-29
> **linuxopjemac said:**
> can't install still:


Odd... I am obviously stabbing in the dark here, no such system to compile test. If this version does not work (updated same place), the source is in /usr/src/applesmc-0.17.0/. :-)

Cheers!

---

### Post by kosumi68 on 2010-10-30
> **ryanczak said:**
> Installed. Will report any problems. Does this new version of applesmc provide better fan control than the old version? I am currently using macfanctld from the mactel ppa. Is it still required? 


Thanks! Yes, those are still required.

---

### Post by kosumi68 on 2010-11-01
Alright, a week of testing, resulting in one reported compile regression on older systems. Since things seem to work satisfactorily, the new 0.17.0 has been pushed to the mactel repo and will be available shortly.

Thanks for testing!

---

### Post by linuxopjemac on 2010-11-01
I hope it will install on my MacBook 2,1.

---

### Post by kosumi68 on 2010-11-01
> **linuxopjemac said:**
> I hope it will install on my MacBook 2,1.

Yes, that will be interesting - it is available now.

---

### Post by linuxopjemac on 2010-11-01
I am still on Lucid...That is probably the reason it didn't install?

---

### Post by kosumi68 on 2010-11-01
> **linuxopjemac said:**
> I am still on Lucid...That is probably the reason it didn't install?

Yes - it does not compile, although I was not sure if the last modification made it compile? There is no real reason for it not to work, it is just a matter of some new preferences regarding debug output which breaks older kernel compilation.

---

### Post by kosumi68 on 2010-11-01
Just installed the package on a lucid machine (amd64), worked fine.

---

### Post by swejap on 2010-11-01
On macbook 5,1 running ubuntu 10.10 I get this message

> 
swejap@ubuntu:~$ dmesg | grep smc
[   12.473363] applesmc: Apple MacBook detected
[   12.855760] applesmc: key=271 fan=1 temp=14 acc=1, light=2, keyb=1
[   12.893899] input: applesmc as /devices/platform/applesmc.768/input/input7
[   12.896554] Registered led device: smc::kbd_backlight
[   12.897040] applesmc: driver successfully loaded
[   14.384434] applesmc: light sensor data length set to 10



I have version 0.17.0-maverick-mactel1 installed.

---

### Post by alexmurray on 2010-11-01
@henrik - thanks for this, I know we discussed it a while back and I never got the time to look at implementing something like this myself - thanks again for your hard work, will have a look at it in the next few days. Any chance of trying to merge this is 2.6.37?

---

### Post by kosumi68 on 2010-11-02
> **alexmurray said:**
> @henrik - thanks for this, I know we discussed it a while back and I never got the time to look at implementing something like this myself - thanks again for your hard work, will have a look at it in the next few days. Any chance of trying to merge this is 2.6.37?

Hi Alex,

Too late for 2.6.37, but we are targeting 2.6.38.

Cheers!

---

### Post by alexmurray on 2010-11-02
No worries - at least it should make it into Natty then automatically. Thanks again for your great work Henrik! You're awesome!

---

### Post by Grumpey on 2010-11-14
dmesg output with macbook pro 5,1

> joe@Grumpey:~$ dmesg | grep applesmc
[   13.773658] applesmc: key=295 fan=2 temp=20 acc=1 lux=2 kbd=1
[   13.835947] input: applesmc as /devices/platform/applesmc.768/input/input7
[   15.012823] applesmc: light sensor data length set to 10
[   69.878050] applesmc: F1Mn: write arg fail
[  190.612018] applesmc: FS! : read arg fail
[  487.344066] applesmc: F1Mn: write arg fail
[  894.696215] applesmc: FS! : read arg fail
[  965.135513] applesmc: FS! : read arg fail
[ 1689.313466] applesmc: FS! : read arg fail
[ 2006.141764] applesmc: F1Mn: write arg fail

---

### Post by Nikos.Alexandris on 2010-11-22
> **Grumpey said:**
> dmesg output with macbook pro 5,1

```
[    3.112336] apple 0003:05AC:8242.0001: hiddev96,hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[    3.675403] apple 0003:05AC:0237.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
[    4.175090] apple 0003:05AC:0237.0003: hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input1
[   29.071667] applesmc: key=295 fan=2 temp=20 acc=1 lux=2 kbd=1
[   29.167830] input: applesmc as /devices/platform/applesmc.768/input/input10
[   36.500320] applesmc: light sensor data length set to 10
[  799.796756] applesmc: TTF0: read arg fail
[ 1010.970612] applesmc: F1Mn: write arg fail
[ 1362.874841] applesmc: FS! : read arg fail
[ 1377.977371] applesmc: F1Mn: write arg fail
[ 1724.729971] applesmc: FS! : read arg fail
[ 1830.266367] applesmc: F1Mn: write arg fail
[ 2187.048148] applesmc: FS! : read arg fail
[ 2292.616520] applesmc: FS! : read arg fail
[ 2297.669956] applesmc: F1Mn: write arg fail
[ 2533.893095] applesmc: F1Mn: write arg fail
[ 2569.093167] applesmc: Th2H: read arg fail
[ 2649.509769] applesmc: FS! : read arg fail
[ 3272.767878] applesmc: F1Mn: write arg fail
[ 3408.525557] applesmc: FS! : read arg fail
[ 3524.132284] applesmc: F1Mn: write arg fail
[ 3574.467444] applesmc: FS! : read arg fail
[ 3946.506710] applesmc: TG0F: read arg fail
[ 5438.595950] applesmc: FS! : read arg fail
[ 5740.036324] applesmc: F1Mn: write arg fail
[ 6237.357676] applesmc: FS! : read arg fail
[ 6473.465025] applesmc: F1Mn: write arg fail
[ 6719.709573] applesmc: FS! : read arg fail
[ 6790.067496] applesmc: FS! : read arg fail
[ 6810.204531] applesmc: FS! : read arg fail
[ 6875.543699] applesmc: F1Mn: write arg fail
[ 6971.053833] applesmc: F1Mn: write arg fail
[ 7167.111631] applesmc: FS! : read arg fail
[ 7217.397236] applesmc: F1Mn: write arg fail
[ 7539.029178] applesmc: FS! : read arg fail
[ 7579.256481] applesmc: FS! : read arg fail
[ 7624.557263] applesmc: F1Mn: write arg fail
[ 7674.818481] applesmc: FS! : read arg fail
[ 8066.750447] applesmc: FS! : read arg fail
[ 8137.140112] applesmc: FS! : read arg fail
```

Also, [COLOR="Blue"]without the battery[/COLOR], the command ```
sensors
``` reports ```
TB0T:       +129.0°C                                    
TB1T:       +129.0°C                                    
TB2T:       +129.0°C                                    
TB3T:       +128.0°C
[...]
```

So **macfanctld** throttles up to max fan speed. Needed to adjust the **/etc/macfanctl.conf** to low down the fans, i.e. I added ```
exclude: 1 2 3 4
```

---

### Post by kosumi68 on 2010-11-22
Hi Nikos,

Thanks for the report! Did you get similar errors with the old module? It appears the failures are frequent but still random. Does it work sometimes, or failure each time? Did the values of TB0T etc have different values with the old module?

---

### Post by Nikos.Alexandris on 2010-11-22
Hi!

> Did you get similar errors with the old module?

As far as I remember, never.

> It appears the failures are frequent but still random. Does it work sometimes, or failure each time?

Till now, as many times as I have checked **dmesg** I always read lots of **read/write arg fail**.

> Did the values of TB0T etc have different values with the old module?

I think yes, i.e., I work mostly with the battery dettached (the last years) and the fans are at full-speed since last week(s).

Cheers

---

### Post by kosumi68 on 2010-11-22
> **Nikos.Alexandris said:**
> 
As far as I remember, never.


Trying to frame this problem further, did you by any chance start using macfanctld at around that time too? What happens (in dmesg) if you perform these commands manually? Unless you already did,
```

sudo -i
cd /sys/devices/platform/applesmc.768/
cat fan2_manual
cat fan2_min
echo 4000 > fan2_input
cat fan2_min
echo your_default_value > fan2_input
cat fan2_min

```

Thanks!

---

### Post by Nikos.Alexandris on 2010-11-22
```
Till now, as many times as I have checked **dmesg** I always read lots of **read/write arg fail**.
```

To make this more clear, I mean "till now = since last week(s) with the new applesmc". Sorry for not being precise.

---

### Post by Nikos.Alexandris on 2010-11-22
> **kosumi68 said:**
> Trying to frame this problem further, did you by any chance start using macfanctld at around that time too? What happens (in dmesg) if you perform these commands manually? Unless you already did,
```

sudo -i
cd /sys/devices/platform/applesmc.768/
cat fan2_manual
cat fan2_min
echo 4000 > fan2_input
cat fan2_min
echo your_default_value > fan2_input
cat fan2_min
```


I started using **macfanctld** in the summer (...dunno when exactly, August?). The thing with the above commands is the following (me thinks):
```
-r--r--r-- 1 root root 4096 2010-11-22 22:52 fan1_input
-r--r--r-- 1 root root 4096 2010-11-22 22:52 fan2_input
```

Those input files are read-only! Otherwise, the **fan2_manual** is always 0 and **fan2_min** changes. Should I change owner permissions?

---

### Post by kosumi68 on 2010-11-23
> **Nikos.Alexandris said:**
> I started using **macfanctld** in the summer (...dunno when exactly, August?). The thing with the above commands is the following (me thinks):
```
-r--r--r-- 1 root root 4096 2010-11-22 22:52 fan1_input
-r--r--r-- 1 root root 4096 2010-11-22 22:52 fan2_input
```

Those input files are read-only! Otherwise, the **fan2_manual** is always 0 and **fan2_min** changes. Should I change owner permissions?

Yes, fanX_manual, fanX_min and fanX_output should all be read-write. This is odd, they should definitely appear as rw, unless you changed them. A
```

sudo rmmod applesmc; sudo modprobe applesmc

```
should yield rw permissions on those files.

---

### Post by Nikos.Alexandris on 2010-11-23
> **kosumi68 said:**
> fanX_manual, fanX_min and fanX_output should all be read-write.

Yep, those files were ok. All of it is ```
/sys/devices/platform/applesmc.768$ ll fan*
-r--r--r-- 1 root root 4096 2010-11-23 12:34 fan1_input
-r--r--r-- 1 root root 4096 2010-11-23 12:34 fan1_label
-rw-r--r-- 1 root root 4096 2010-11-23 12:52 fan1_manual
-r--r--r-- 1 root root 4096 2010-11-23 12:52 fan1_max
-rw-r--r-- 1 root root 4096 2010-11-23 12:52 fan1_min
-rw-r--r-- 1 root root 4096 2010-11-23 12:52 fan1_output
-r--r--r-- 1 root root 4096 2010-11-23 12:52 fan1_safe
-r--r--r-- 1 root root 4096 2010-11-23 12:34 fan2_input
-r--r--r-- 1 root root 4096 2010-11-23 12:34 fan2_label
-rw-r--r-- 1 root root 4096 2010-11-23 12:52 fan2_manual
-r--r--r-- 1 root root 4096 2010-11-23 12:52 fan2_max
-rw-r--r-- 1 root root 4096 2010-11-23 12:52 fan2_min
-rw-r--r-- 1 root root 4096 2010-11-23 12:52 fan2_output
-r--r--r-- 1 root root 4096 2010-11-23 12:52 fan2_safe
```

The reason I only posted the ***input** files is because the **echo**ing commands (previous post) where targetting, well, the ***input** file(s). I did not change those files.

TB* sensors still show 129 degrees (without the battery of course). When the battery is plugged-in it looks fine, i.e. ```
TB0T:        +20.0°C                                    
TB1T:        +20.0°C                                    
TB2T:        +19.5°C                                    
TB3T:        +19.8°C
```

Removing and loading again the applesmc module does not change the permissions of the ***input** files (as expected I guess?).

---

### Post by kosumi68 on 2010-11-23
I see, so with/without battery affects the readings, which should be ok. What I can see, the remaining question is whether the read/write failures are random or occur every time. Your estimate here would be most valuable. I am also trying to understand the amount of read/writes to fanX_manual. Since writing this particular value changes the internal fan handling in the SMC, it is probably a good idea to exclude it from the control loop in macfanctld.

Thanks for testing!

---

### Post by Nikos.Alexandris on 2010-11-23
> **kosumi68 said:**
> I see, so with/without battery affects the readings, which should be ok.

Yes. But, why set to 129 degrees when readings are not available (unplugged battery)? What is the motivation behind this? Can it not be set to N/A or the like? Or something that **macfanctld** will understand and ignore automatically?

Currently, the user *should* change the exclude option in **/etc/macfanctld.conf** each time the battery is being un-/plugged.

> What I can see, the remaining question is whether the read/write failures are random or occur every time. Your estimate here would be most valuable.

Hmm... I was about to say it is "default" but now I am unsure. Loading and unloading **applesmc** should produce the same list of **read arg fail** messages right? Well, it does not. The only messages added after **rmmod** and **modprobe** are

```
[ 8836.704892] applesmc: key=295 fan=2 temp=20 acc=1 lux=2 kbd=1
[ 8836.735361] input: applesmc as /devices/platform/applesmc.768/input/input11
[ 8837.423779] applesmc: light sensor data length set to 10
```

> I am also trying to understand the amount of read/writes to fanX_manual. Since writing this particular value changes the internal fan handling in the SMC, it is probably a good idea to exclude it from the control loop in macfanctld.

Not sure if I am able to help with this - also, currently I am a bit confused with other stuff and it will take me to dive a bit more in the *SMC and fan control* logic :-)

Cheers!

---

### Post by kosumi68 on 2010-11-23
> **Nikos.Alexandris said:**
> Yes. But, why set to 129 degrees when readings are not available (unplugged battery)? What is the motivation behind this? Can it not be set to N/A or the like? Or something that **macfanctld** will understand and ignore automatically?


It seems the information is not available, unfortunately - the readings are simply what you get from the smc. Just to make sure: you plug/unplug the battery with the machine off, right?

> 

Not sure if I am able to help with this - also, currently I am a bit confused with other stuff and it will take me to dive a bit more in the *SMC and fan control* logic :-)

Cheers!

No problem, I think we are making steady progress - thanks! :-)

---

### Post by Nikos.Alexandris on 2010-11-23
> **kosumi68 said:**
> It seems the information is not available, unfortunately - the readings are simply what you get from the smc. Just to make sure: you plug/unplug the battery with the machine off, right?


Not really... 8-[ But even booting with the battery not present gives the same 129 degrees readings.

Thanks for all the work :-)

---

### Post by mikael.karon on 2012-07-03
Not sure if this thread is dead (and if the solution is presented somewhere else) but I'm having the same problem on my mbp 6,2 12.04.

---

### Post by wildmanne39 on 2012-07-05
Old thread closed.

---

