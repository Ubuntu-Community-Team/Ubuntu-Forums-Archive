---
title: "Cannot make lm-sensors work!"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by theadventuresofanidealist on 2007-04-26
im running xubuntu on a sony vaio pcg fx-340.
i followed this tutorial [here]("http://ubuntuforums.org/showthread.php?t=2780") and then this one [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29") and i can't make them work.
heres a copy of some of what i did:

```
user@ubuntu:~/Desktop$ sudo ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': File exists
user@ubuntu:~/Desktop$ sudo sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801BA ICH2
Use driver `i2c-i810' for device 0000:00:02.0: Intel 82815 GMCH

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
Module `i2c-i810' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1810
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4f
y
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x57
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Next adapter: I810/I815 DDC Adapter
Do you want to scan it? (YES/no/selectively): 
Next adapter: I810/I815 I2C Adapter
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x75

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
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 1810'
    Busdriver `i2c-i801', I2C address 0x57
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
user@ubuntu:~/Desktop$ sudo /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
user@ubuntu:~/Desktop$ sudo sensors -s
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
user@ubuntu:~/Desktop$ 
```

---

### Post by igknighted on 2007-04-26
sounds like you just don't have any sensors installed for your system to detect.  Are you sure you have sensors installed?  Also, do you have to boot with any acpi=off options or similar?  This could possibly interfere.

---

### Post by theadventuresofanidealist on 2007-04-26
i have no idea how to install the sensors, i just followed to howtos to install the lm-sensors package.
How do i check if i have any sensors installed?
As for the acpi=off i have no idea either. where do i check that?

---

### Post by igknighted on 2007-04-26
> **theadventuresofanidealist said:**
> i have no idea how to install the sensors, i just followed to howtos to install the lm-sensors package.
How do i check if i have any sensors installed?
As for the acpi=off i have no idea either. where do i check that?

I would check the manual for your computer about sensors, or email the manufacturer.  As for acpi=off, if you didn't add it specifically as a boot parameter when you installed then it isn't an issue.

---

### Post by AlexenderReez on 2007-04-26
i think this guide still works.....

> [http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml](http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml)

---

### Post by theadventuresofanidealist on 2007-04-26
> I would check the manual for your computer about sensors, or email the manufacturer. As for acpi=off, if you didn't add it specifically as a boot parameter when you installed then it isn't an issue.

Ill check on the manual, im using sony pcg fx-340 with xubuntu feisty fawn...with 128mb

---

### Post by thelocust on 2007-05-31
Did you forget to modprobe?
```

sudo modprobe ic2-i801
sudo modprobe eeprom
```

---

