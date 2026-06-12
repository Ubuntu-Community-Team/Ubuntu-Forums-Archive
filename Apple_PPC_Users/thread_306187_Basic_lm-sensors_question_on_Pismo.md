---
title: "Basic lm-sensors question on Pismo"
date: 2006-11-24
forum: Apple PPC Users
---

### Post by dpny on 2006-11-24
Has anyone gotten lm-sensors, or any CPU temp monitor, to work on a Pismo? I have googled and searched and seem to find people who have gotten it to work but can't find an explanation of how.

---

### Post by stream303 on 2006-11-25
I don't own a pismo, but an iMac Ubuntu 6.10 and got the "sensors-applet" from the universe repository to work pretty well.

---

### Post by dpny on 2006-11-30
> **stream303 said:**
> I don't own a pismo, but an iMac Ubuntu 6.10 and got the "sensors-applet" from the universe repository to work pretty well.

Crashed on my machine. If I look at /proc/cpuinfo there is temperature info, but lm-sensors seems to bork. I've installed it, etc.

---

### Post by dpny on 2006-12-03
So, more info:

Been googling around about lm-sensors. I have run sensors-detect and get:

```
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
```

./mkdev.sh gives:

```
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
```

Running sensors-detect now gives:

```
sudo sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:18)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no): y
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: mac-io 0
Do you want to scan it? (YES/no/selectively): y
Client at address 0x56 can not be probed - unload all client drivers first!

Next adapter: uni-n 1
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x49
Probing for `National Semiconductor LM75'... Failed!
Probing for `National Semiconductor LM77'... Failed!
Probing for `Dallas Semiconductor DS1621'... Failed!
Probing for `National Semiconductor LM92'... Failed!
Probing for `National Semiconductor LM76'... Failed!
Probing for `Maxim MAX6633/MAX6634/MAX6635'... Failed!
Client at address 0x50 can not be probed - unload all client drivers first!

Next adapter: uni-n 0
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x49
Probing for `National Semiconductor LM75'... Failed!
Probing for `National Semiconductor LM77'... Failed!
Probing for `Dallas Semiconductor DS1621'... Failed!
Probing for `National Semiconductor LM92'... Failed!
Probing for `National Semiconductor LM76'... Failed!
Probing for `Maxim MAX6633/MAX6634/MAX6635'... Failed!
Client at address 0x50 can not be probed - unload all client drivers first!

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): y
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
```

I'm not sure what 'unload client drivers' first means. However, the first time I ran sensors-detect it ceated the following to add to /etc/modules:

```
# Generated by sensors-detect on Sun Dec  3 15:56:40 2006
# I2C adapter drivers
# modprobe unknown adapter uni-n 0
# modprobe unknown adapter uni-n 1
# modprobe unknown adapter mac-io 0
# I2C chip drivers
eeprom
```

And added i2c_keywest to /etc/modules. Still no sensors are working.

So. . .

Can anyone help me decipher this? I have seen reference to a kernel module called "therm_pm72" but I don't know if it will work for my machine. Anyone have any ideas?

---

