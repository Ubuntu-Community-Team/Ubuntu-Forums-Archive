---
title: "Problem with fan"
date: 2010-04-29
forum: Apple Hardware Users
---

### Post by egalois on 2010-04-29
Hi there,

I installed on my iMac g5 ppc ubuntu 10.04. Unfortunately there's a problem with my fan. It's going on as soon as I logged in. It's a horrible din. I installed the package lm-sensors but it told me, that there are no sensors!

```
icolas@ubuntu:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nicolas@ubuntu:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# DMI data unavailable, please consider installing dmidecode 2.7
# or later for better results.

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Next adapter: radeonfb monid (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: radeonfb dvi (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: radeonfb vga (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: radeonfb crt2 (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: smu 14 (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: smu 11 (i2c-5)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x29
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x4a
Handled by driver `windfarm_lm75_sensor' (already loaded), chip type `wf_lm75'
    (note: this is probably NOT a sensor chip!)

Next adapter: mac-io 0 (i2c-6)
Do you want to scan it? (YES/no/selectively): y

Next adapter: u4 1 (i2c-7)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x48
Handled by driver `windfarm_lm75_sensor' (already loaded), chip type `wf_lm75'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x49
Handled by driver `windfarm_lm75_sensor' (already loaded), chip type `wf_lm75'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x4c
Handled by driver `windfarm_max6690_sensor' (already loaded), chip type `wf_max6690'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x4e
Handled by driver `windfarm_max6690_sensor' (already loaded), chip type `wf_max6690'
    (note: this is probably NOT a sensor chip!)

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
```  

I hope there's someone, who can help me! I don't know how I can solve this problem. Thx for your help!

---

### Post by linuxopjemac on 2010-04-29
Give us the output of

```
uname -r
sudo dmidecode -s system-product-name
lsmod | grep windfarm

```

I like to see if you have a windfarm module loaded

You will probably need the windfarm-pm121 kernel module:
[https://wiki.ubuntu.com/iMacG5iSight?action=show&redirect=iMacG5revC](https://wiki.ubuntu.com/iMacG5iSight?action=show&redirect=iMacG5revC)

---

### Post by egalois on 2010-04-30
here is the output:

```
nicolas@ubuntu:~$ uname -r
2.6.32-21-powerpc64-smp
nicolas@ubuntu:~$ sudo dmidecode -s system-product-name
sudo: dmidecode: command not found
nicolas@ubuntu:~$ lsmod | grep windfarm
windfarm_smu_sensors     8567  2 
windfarm_smu_controls     7629  0 
windfarm_max6690_sensor     5588  0 
windfarm_lm75_sensor     6091  0 
windfarm_smu_sat        8496  0 [permanent]
windfarm_cpufreq_clamp     3805  0 
windfarm_pid            3553  0 
windfarm_core          15947  6 windfarm_smu_sensors,windfarm_smu_controls,windfarm_max6690_sensor,windfarm_lm75_sensor,windfarm_smu_sat,windfarm_cpufreq_clamp
nicolas@ubuntu:~$ 

```but unfortunately it didn't found dmidecode.

I try to install the patch:

```
 
root@ubuntu:/home/nicolas# patch -p0 < Desktop/windfarm-pm121.patch
patching file b/arch/powerpc/configs/g5_defconfig
Hunk #1 FAILED at 667.
1 out of 1 hunk FAILED -- saving rejects to file b/arch/powerpc/configs/g5_defconfig.rej
patching file b/drivers/macintosh/Kconfig
Hunk #1 FAILED at 234.
1 out of 1 hunk FAILED -- saving rejects to file b/drivers/macintosh/Kconfig.rej
patching file b/drivers/macintosh/Makefile
Hunk #1 FAILED at 42.
1 out of 1 hunk FAILED -- saving rejects to file b/drivers/macintosh/Makefile.rej
patching file b/drivers/macintosh/windfarm_lm75_sensor.c
Hunk #1 FAILED at 127.
1 out of 1 hunk FAILED -- saving rejects to file b/drivers/macintosh/windfarm_lm75_sensor.c.rej
patching file b/drivers/macintosh/windfarm_max6690_sensor.c
Hunk #1 FAILED at 77.
Hunk #2 FAILED at 138.
2 out of 2 hunks FAILED -- saving rejects to file b/drivers/macintosh/windfarm_max6690_sensor.c.rej


```

but unfortunately without any success.

---

### Post by egalois on 2010-05-01
Is there someone, who could tell me, what's going wrong with my try to install the patch.

Thx for help!

---

### Post by linuxopjemac on 2010-05-02
to find out your model
```
cat /proc/cpuinfo
```

---

### Post by linuxopjemac on 2010-05-02
I would contact Benjamin Herrenschmid, he is responsible for PPC kernel patches.
[http://penguinppc.org/historical/benh/](http://penguinppc.org/historical/benh/)
[email]benh@kernel.crashing.org[/email]

Please report if you fixed it how you did it. I want to know it too.

---

### Post by selittl on 2010-07-24
I am having the same issue.  Problem is that I'm a noob and don't know how to build and deliver the patch to my system.  Can someone let me know how to do this?

---

