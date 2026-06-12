---
title: "acpi thermal"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by mgvbstar on 2007-04-27
I have feisty on an acer aspire 5673 which has a core duo 1.66 ghz.  When I do acpi -V is get 

```
acpi -V
     Battery 1: charging, 93%, 00:00:12 until charged
     Thermal 1: ok, 49.0 degrees C
  AC Adapter 1: on-line
```

What is thermal 1 the temperature of?  
The value of Thermal 1 matches the value in /proc/acpi/thermal_zone/THRM/temperature if this helps.
Also, if it isnt the temp of my CPU, is there any way for me to get the temp of the CPU (lm-sensors does not seem to work)?

---

### Post by tgalati4 on 2007-04-27
It's probably a thermal diode under the processor.  What errors did you experience with lm-sensors?

I trust that you tried:

sudo modprobe i2c-dev           (adds a temporary i2c device that is used for probing)
sudo sensors-detect               (answer yes to most of the questions)
more /etc/modules                   (to confirm that the i2c and thermal chip modules were added automatically)
sudo sensors -s                       (does some final tweaking of your sensors configuration file)
sensors                                    (to see the output of any sensors found)
(install your favorite panel app to monitor)

---

### Post by mgvbstar on 2007-04-27
Thanks for the reply.

WIth lm-sensors, I followed the guide [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29").

The output from running sensors-detect is 

```

 sudo sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH7

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 18c0
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x08
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x52
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0xec11
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87591 Super IO'                         
    (but not activated)
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0xec11
Trying family `VIA/Winbond/Fintek'...                       Yes
Found unknown chip with ID 0xec11
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 18c0'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)
  * Bus `SMBus I801 adapter at 18c0'
    Busdriver `i2c-i801', I2C address 0x52
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)y


```

But then when I do  "sudo /etc/init.d/module-init-tools" followed by  "sudo sensors -s" and I get 

```
 sudo sensors -s
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

---

### Post by tgalati4 on 2007-04-27
You have new hardware.  Chances are that lm-sensors doesn't yet support your hardware.

What version of sensors are you running?  (sensors -v)

I am running:

sensors version 2.9.2 with libsensors version 2.9.2

on a Dapper 6.06.1, whitebox desktop machine.  The latest version (lm-sensors.org) is:

lm_sensors v2.10.3 and i2c v2.10.2

Your SMB bus chip looks like a Winbond PC87591 according to your sensor-detect output:

Found `Nat. Semi. PC87591 Super IO'                         
    (but not activated)

According to this page: 

[http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

It is not supported.  So that is a dead-end.

Try searching google for intel core duo temperature monitoring and see what comes up.

For now, you have only one sensor (ACPI) to monitor, but at least it's something to look at on your panel.  You can tweak fan speeds and set alarms (including sending emails to yourself) based on that one sensor.  You might contact Acer tech support and they might tell you what physically is being monitored.

Good luck.

---

### Post by mgvbstar on 2007-04-27
Thanks! I will go ahead and contact acer to find out what temp is being monitored, and will wait for lm-sensors to support my hardware (currently i am using sensors version 2.10.1 with libsensors version 2.10.1).

Thanks for the help - this is why i LOVE ubuntu!

---

### Post by tgalati4 on 2007-04-27
Intel has been pretty good with giving support to the Linux community.  They have been busy trying to get Mac Book Pro's to work and reengineer their entire processor line.  It won't take long for some nifty tools to come out of Intel for tweaking the Core series processor.

Regardless, keep an eye on processor temperature, because all it takes is one run-away process to heat up your motherboard.  The processor can take the heat, it's the motherboard that warps and causes problems downstream.  I know the early mac book pros had lots of heat issues.

---

### Post by ppan76 on 2007-04-28
I have the Intel 82801G Chipset and according according to the wiki is supported using the i2c-i801 module. However I got the same issue as you.

---

### Post by loko on 2007-04-28
i also get problems with the core duo.

you can find a solution for this problem here

[http://ubuntuforums.org/showthread.php?p=2422094#post2422094]("http://ubuntuforums.org/showthread.php?p=2422094#post2422094")

---

### Post by ppan76 on 2007-04-28
You beat me to the answer by 5 minutes.
But I am afraid to patch and recompile kernel as I dont want to break other stuff.

---

