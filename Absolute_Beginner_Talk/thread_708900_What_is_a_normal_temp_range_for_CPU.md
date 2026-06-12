---
title: "What is a normal temp range for CPU?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-02-26
I just don't have any concept of what is hot or cold for a cpu.

I have conky and added a line for acpi temp and it outputs 60, usually. I should hope that isn't farenheit, as that's less than room temperature! But 60 C is pretty hot, I imagine. Is that normal?

---

### Post by glennric on 2008-02-26
It should be celsius, and yes that is a little hot.  My cpu usually runs around 50-55.  With a high load it gets higher though.

---

### Post by LowSky on 2008-02-26
depending on the processor and the heatsink your temp could be fine

old Pentium 4s ran very warm at or around 55'C
Most chips Run at or around 40-45'C
Mine is running at 38'C

I think its my massive schythe katana heat sink.

---

### Post by Pogeymanz on 2008-02-26
Does it matter that it's a laptop? Do laptops tend to run hotter?

---

### Post by 3rdalbum on 2008-02-26
I imagine that 60 degrees celcius is very high for a laptop. Laptops use low-power processors which should run cooler (but with lower performance).

What should a Core 2 Duo 65nm run at in terms of temperature? Lm-sensors says it's using unreliable methods to determine the temperature, and then tells me that it's running at 16 degrees Celcius.

---

### Post by northern lights on 2008-02-26
My laptop (Asus W1/N, PM1.6) idles at 55 centigrade in Ubuntu, Knoppix & WinXP. Only if clocked down to 600Mhz do I get it to under 45 degrees.

When running a demanding graphical application (i.e. a game) I got it up to 89 in summer. I know that ain't healthy, but it survived. Anyways, I stopped worrying about 60+ degrees 2 years back. That might be quite daft also, but I did.

---

### Post by igknighted on 2008-02-26
> **3rdalbum said:**
> I imagine that 60 degrees celcius is very high for a laptop. Laptops use low-power processors which should run cooler (but with lower performance).

What should a Core 2 Duo 65nm run at in terms of temperature? Lm-sensors says it's using unreliable methods to determine the temperature, and then tells me that it's running at 16 degrees Celcius.

Actually, laptops use low power chips because they would  burn up otherwise.  The problem is with the airflow, in such a tight space there is almost none.  And you can't use a big heatsink (space) or a big fan (power drain) to keep it cool.  Laptops typically run 10-20 degrees hotter (in my experiences) than similar desktop chips.

EDIT: A c2d at stock clock and voltages should and a decent aftermarket cooler should idle near 30c, and should max out somewhere between 40c and 50c.  My desktop (see spec below) averaged a couple degrees over room temp for a while, and even now that it's OC'd, it takes some real strain (read: crysis or cod4) to push it over 35c, but the c2d's run faster and also slightly hotter than their AMD rivals.

---

### Post by Lvcoyote on 2008-02-26
My laptop runs a tad cooler, but not much.  If the Laptop has any age to it or is used quite frequently you may want to open it up and see of your CPU heatsink is clogged with dust, give it a good cleaning.

---

### Post by Paqman on 2008-02-26
> **igknighted said:**
> Laptops typically run 10-20 degrees hotter (in my experiences) than similar desktop chips.

Sounds about right. Mine's been known to hit 80 on occasion. Normally that's when it's hard some of it's intakes/vents obstructed somehow. You can really see the temp climb in the first few minutes of use, and it reacts strongly to changes in load. My desktop, by comparison is rock-steady at around 40 degrees no matter what I do to it.

---

### Post by herbster on 2008-02-27
Ouch, 60 is pretty high. I'm on my sister's Vista laptop right now and just checked, it's going at about 39-40C and I just started a bunch of intensive apps. My desktop is a Q6600 that idles at about 28C and I have not seen it ever go higher than 37C.

However, don't be too panicked, as CPUs can handle a lot more than the massive "keep my pc iced down" crowd of box-enthusiasts will have you believe. Still, for the life of the CPU you'll want to keep 'er cooler the better.

---

### Post by meindian523 on 2008-02-27
Is a maximum of 70 degrees C okay for a Pentium D 2.80 GHz.When I first boot up,the BIOS starts of with about 48 degrees or so.Lm-sensors don't work on my box,so the 70 degrees figure is after  I go into the BIOS after shutting down.

---

### Post by motion parallax on 2008-02-27
I've been having similar issues.  My laptop runs around 54 C at max performance.  Been scaring me a little, so I bought one of those chill pads.  Targus Tornado.  Seated on my lap, the temp came down to 31 C.  I returned it for a Belkin (mostly curious) and now the temp stays around 48 C.  I'm getting the Targus back.

---

### Post by PurposeOfReason on 2008-02-27
I'm at 47C on my laptop and 32C on the desktop.

---

### Post by meindian523 on 2008-02-27
Can someone tell me what does the THRM reading on Gkrellm show?Temperature of CPU,HDD,what?
And also whether 70 degrees is OK for a Pentium D?

---

### Post by motion parallax on 2008-02-27
70 C for a laptop is a little high.  I would take the unit in to get cleaned (unless you want to do it yourself).  Try a cooling pad.  They only cost about 30 bucks, well worth the money.

---

### Post by meindian523 on 2008-02-27
Nopes,it's a desktop.Now?

---

### Post by Placified on 2008-02-27
Mine runs about 40C.  Intel I would be nervous after 46 or 47C.  AMD's can usualy run hotter and stay stable if has been my experience that their ceiling is 55-60C.  I would not recomend Running that hot constantly, but for short heavy loads it would be fine for an AMD.  So 45-50 average for AMD and 40-45 for INTEL.

---

### Post by herbster on 2008-02-27
70C on a desktop?! Do you have a fan on your CPU or just a heatsink? If just a heatsink definitely get yourself a heatsink/fan. How long have you been using it? You may need to apply some thermal paste to it.

Also, what is the temperature of your motherboard? May want to check the cooling situation of your case, if you have fans and how many there are/how they are placed.

---

### Post by 3rdalbum on 2008-02-27
I suspect my C2D is running at approximately 35 degrees celcius with stock cooling.

Can anyone tell me if turning off a core will make the temperature drop further?

---

### Post by igknighted on 2008-02-27
> **3rdalbum said:**
> I suspect my C2D is running at approximately 35 degrees celcius with stock cooling.

Can anyone tell me if turning off a core will make the temperature drop further?

Probably... but why?  35c is nothing to be concerned about, and if you are really paranoid, an upgrade for the cpu cooler would only run like 15-25 USD.  You paid for two cores... I'd use them.

---

### Post by motion parallax on 2008-02-27
70 C on a desktop?  You're kidding, right?  

Check to make sure the fan is working.  Buy a bigger fan.  Do a google search; it'll give you a few hundred things to do to improve heat.  

If nothing else, remove the cover of your computer and put a small floor fan next to it.  Better than a dead PC.

---

### Post by herbster on 2008-02-27
You really want to turn off a core to get it cooler than 35C? :( That's nothing to worry about.

---

### Post by ramjet_1953 on 2008-02-27
Instead of just chasing our tales and quoting urban myths, all you have to do is go to the manufacturer's website and check out the specs of your particular processor.

My laptop has a Pentium M processor.

Here is a link for temperatures:

[http://www.intel.com/support/processors/mobile/pm/sb/cs-007971.htm](http://www.intel.com/support/processors/mobile/pm/sb/cs-007971.htm)

Note that is says the absolute max is 100 C.  Ow!

However anything around 60 - 70 C for a laptop when under stress should be OK.

My laptop idles along in the tropics around 53 C and peaks out around the high 60' s, which should be well within the tolerable zone.

Regards,
Roger :cool:

---

### Post by meindian523 on 2008-02-27
> **herbster said:**
> 70C on a desktop?! Do you have a fan on your CPU or just a heatsink? If just a heatsink definitely get yourself a heatsink/fan. How long have you been using it? You may need to apply some thermal paste to it.

Also, what is the temperature of your motherboard? May want to check the cooling situation of your case, if you have fans and how many there are/how they are placed.

I have two fans.One is the PS fan and another on the case.Been using it since Sept 06.Now how do I get the temperature of the motherboard?Please note that lm-sensors are not available for the CPU.(Atleast,I think so)If anybody can contradict that,I would be very happy.BTW,am using a D101GGC Intel motherboard.

> **motion parallax said:**
> 70 C on a desktop?  You're kidding, right?  

Check to make sure the fan is working.  Buy a bigger fan.  Do a google search; it'll give you a few hundred things to do to improve heat.  

If nothing else, remove the cover of your computer and put a small floor fan next to it.  Better than a dead PC.

Nopes,I'm not kidding,but it might be worthwhile to note I said MAX temperature.That was after some make and make install once and otherwise after shutting down from a Compiz-Fusion session.

I'm an absolute hardware newbie,so please go slow and in easy language.I hardly know anything about hardware except that there's a CPU,motherboard(god knows what's in there and how it works),a chip of RAM and a power supply.Never opened a case of a computer in my life!

I went to the page for Pentium D at the Intel website as said by ramjet_1953 and I found that the max temp for my processor (Pentium D 920)(2.80 GHz) was 62.1 degrees if I've read the table right.:(

---

### Post by meindian523 on 2008-02-27
And of course,I live in the tropics.And I guess that this is the relevant page on Intel's website.

[http://www.intel.com/cd/channel/reseller/asmo-na/eng/216412.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/216412.htm)

coz my System tab on System Monitor shows

Processor 0:Intel(R) Pentium(R) D CPU 2.80GHz
Processor 1:Intel(R) Pentium(R) D CPU 2.80GHz

---

### Post by herbster on 2008-02-27
Do you know how to go into your BIOS? When you start up your computer you can hit either F1 or DEL usually and get in there. Then depending on the bios you will be looking for an option called Hardware Monitor.

And are you saying lm sensors does not work for your CPU or for any CPU? I am 99% sure it will work for your box just fine. Have you tried installing it?

---

### Post by meindian523 on 2008-02-27
Yup,F2 is the key for my BIOS.I guess you didn't read my original post which said "in the BIOS after shutting down" and "in the BIOS on boot"

I did install it.
```

easwarh@l1nuxr0cks:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
easwarh@l1nuxr0cks:~$sudo sensors-detect
Password:
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc ATI SMBus

We will now try to load each adapter module in turn.
Module `i2c-piix4' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus PIIX4 adapter at 0b00
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791D'...                            No
Client found at address 0x50
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
Found unknown chip with ID 0x7803
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x7803
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
  * Bus `SMBus PIIX4 adapter at 0b00'
    Busdriver `i2c-piix4', I2C address 0x50
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
i2c-piix4
# Chip drivers
eeprom
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)y
easwarh@l1nuxr0cks:~$ 

```

Then I again did after all this
```
easwarh@l1nuxr0cks:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
easwarh@l1nuxr0cks:~$ 
```

And this is a vicious circle.That's why I said lm-sensors doesn't work.

---

### Post by meindian523 on 2008-02-27
Just thought of it.I will reboot and now that those kernel modules would be supposedly loaded,I MIGHT just get an output from any sensors which might be there.Apologise for the length of previous post.

---

### Post by meindian523 on 2008-02-27
I rebooted and I'm still stuck at
```

easwarh@l1nuxr0cks:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
easwarh@l1nuxr0cks:~$ 

```
and I went into the BIOS during reboot.My processor fan was running at 3758-3760 RPM.Speeds for front fan and back fan were 0 RPM.And horror of horrors,my processor temperature was 70 degrees WITHOUT compiz-fusion or make && make install.I guess I need serious help with my box.
PS:
Should I make a separate thread for this?

---

### Post by meindian523 on 2008-02-27
I've got to get to college tomorrow,so I must get to sleep now.Thanks for your replies and helpfulness.

---

### Post by Butthead on 2008-02-27
I regularly keep a lit cigar and mug of steaming hot chocolate on top of my CPU.:tongue:

I figure since it'll be horribly obsolete in as little as six months anyway, why should I care if it burns up? :confused:

You people sweat the small stuff too much.:rolleyes:

---

### Post by meindian523 on 2008-02-28
Not everyone can buy a new CPU+motherboard like you every six months,Butthead.You had keep your stiff upper lip out of here.Unless that post was meant as a joke.

---

### Post by geekcliff on 2008-02-28
According to over clockers, 70c is the target figure to keep your cpu temp on or under.:guitar:
 Just thought I'd mention this if anyone cares:biggrin:

---

### Post by talsemgeest on 2008-02-28
I think you should aim to keep your cpu under 50 c when its idling. Mine stays at 30 c whether idling or under stress

---

### Post by geekcliff on 2008-02-28
My PC actually runs at 42 max even under heavy load, but it has got a copper coolermaster heat pipe heat sink that can be used when over clocking, i am thinking of having a go at this, so i did a bit of research and that was the extreme max thats recommended. :confused:

---

### Post by herbster on 2008-02-28
> **Butthead said:**
> I regularly keep a lit cigar and mug of steaming hot chocolate on top of my CPU.:tongue:

I figure since it'll be horribly obsolete in as little as six months anyway, why should I care if it burns up? :confused:

You people sweat the small stuff too much.:rolleyes:

Haha, if that's a joke, great; if not, the 6 months claim is horribly inaccurate.

meridian,

Try:

```
sudo modprobe i2c-sensor
sudo modprobe i2c-viapro
sudo modprobe i2c-isa
sudo modprobe it87
```

Then try sensors again.

---

### Post by Joeb454 on 2008-02-28
According to conky, my laptop idles (and under heavy load too) stays around 53-55 :)

Hope this helps you figure it out :p

---

### Post by Butthead on 2008-02-28
> **meindian523 said:**
> Not everyone can buy a new CPU+motherboard like you every six months,Butthead.You had keep your stiff upper lip out of here.Unless that post was meant as a joke.

So, do you run "worthless" apps like 3D desktop and overclock everything? :confused:

If so, turn them all off.  That'll cut the heat output some. :guitar:

Hint - turning off the computer when it's not being used will extend it's useful lifetime some too.

---

### Post by RedRat on 2008-02-29
OK a newbie here. How exactly do you get the temp of the CPU? Is there a command? I noted that someone said he used acpi temp, I presume in the terminal.

---

### Post by meindian523 on 2008-02-29
> **herbster said:**
> 
meridian,

Try:

```
sudo modprobe i2c-sensor
sudo modprobe i2c-viapro
sudo modprobe i2c-isa
sudo modprobe it87
```

Then try sensors again.

I tried acpi -t following a thread I got when I was trying to make a new thread.these were the results:
```
easwarh@l1nuxr0cks:~$ acpi -t
     Thermal 1: ok, 40.0 degrees C
easwarh@l1nuxr0cks:~$ 
```
What say?

And these were the results of your try:

```
easwarh@l1nuxr0cks:~$ s modprobe i2c-sensor
Password:
FATAL: Module i2c_sensor not found.
easwarh@l1nuxr0cks:~$ s modprobe i2c_sensor
FATAL: Module i2c_sensor not found.
easwarh@l1nuxr0cks:~$ s modprobe i2c-viapro
easwarh@l1nuxr0cks:~$ s modprobe i2c-isa
easwarh@l1nuxr0cks:~$ s modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.20-16-generic/kernel/drivers/hwmon/it87.ko): No such device
easwarh@l1nuxr0cks:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
easwarh@l1nuxr0cks:~$ 

```

> **Butthead said:**
> So, do you run "worthless" apps like 3D desktop and overclock everything? :confused:

If so, turn them all off.  That'll cut the heat output some. :guitar:

Hint - turning off the computer when it's not being used will extend it's useful lifetime some too.

Nopes,I use my 3D enabled desktop only to show off when friends are here.I didn't overclock my processor.As mentioned above,I've never opened a case of a computer in my life,so question f overclocking doesn't arise.

And about turning off the box when not being used,I'm not a uptime fanatic.

#Note:
I have put alias s='sudo' in my .bash_profile.

---

### Post by herbster on 2008-02-29
> **meindian523 said:**
> I tried acpi -t following a thread I got when I was trying to make a new thread.these were the results:
```
easwarh@l1nuxr0cks:~$ acpi -t
     Thermal 1: ok, 40.0 degrees C
easwarh@l1nuxr0cks:~$ 
```
What say?

And these were the results of your try:

```
easwarh@l1nuxr0cks:~$ s modprobe i2c-sensor
Password:
FATAL: Module i2c_sensor not found.
easwarh@l1nuxr0cks:~$ s modprobe i2c_sensor
FATAL: Module i2c_sensor not found.
easwarh@l1nuxr0cks:~$ s modprobe i2c-viapro
easwarh@l1nuxr0cks:~$ s modprobe i2c-isa
easwarh@l1nuxr0cks:~$ s modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.20-16-generic/kernel/drivers/hwmon/it87.ko): No such device
easwarh@l1nuxr0cks:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
easwarh@l1nuxr0cks:~$ 

```

It would appear your hardware isn't cooperating with the lm-sensors drivers. Acpi seems to work, so that's good-- it doesn't work for me, so there you go.

---

### Post by meindian523 on 2008-02-29
Ah,but I shutdown almost immediately and the BIOS says 70 degrees.Now who do I believe?I doubt there can be a jump of 30 degrees within a 15 minutes.

---

### Post by lswest on 2008-02-29
uh, just wanna throw this out there, my laptop CPU (amd turion 64 x2 mobile tl-56 @ 1.8GHz) idles at around 37-38°C and under stress and in a warm room with blocked fanports it can go up to 47-48°C, but never more than that.  My desktop PC (running a P4 2.6GHz, or at the time while i was overclocking a 1.8 to 2.06GHz) it was around about 52°, sometimes even went up to ~65°, but it never really burned up, it had a few scorch marks (the overclocked CPU i replaced ages ago) where the thermal paste had kind of boiled away :P but yeah, that was with a stock cooler.  Just some random infos for ya:P

---

### Post by herbster on 2008-02-29
@meindian523,

The acpi is probably reading your motherboard temp. Try acpi -V and see the output?

---

### Post by meindian523 on 2008-02-29
same output.

---

### Post by RedRat on 2008-02-29
> **herbster said:**
> @meindian523,

The acpi is probably reading your motherboard temp. Try acpi -V and see the output?

Yeah I got exactly the same value as with acpi -t. However, mine comes back with exactly "40.0 degrees C". OK, being a scientist I worry a bit about getting back a value of exactly 40.0. This value has held steady now for over 5 hours. I hope it is right.

---

### Post by Butthead on 2008-02-29
> **lswest said:**
> uh, just wanna throw this out there, my laptop CPU (amd turion 64 x2 mobile tl-56 @ 1.8GHz) idles at around 37-38°C and under stress and in a warm room with blocked fanports it can go up to 47-48°C, but never more than that.  My desktop PC (running a P4 2.6GHz, or at the time while i was overclocking a 1.8 to 2.06GHz) it was around about 52°, sometimes even went up to ~65°, but it never really burned up, it had a few scorch marks (the overclocked CPU i replaced ages ago) where the thermal paste had kind of boiled away :P but yeah, that was with a stock cooler.  Just some random infos for ya:P

Didja ever see how some of these CPU manufacturing plants "stress" test their products?  Basically, they run them for hours in big plexiglass, oven like boxes that get over 200*F.  I hardly believe that someone who has a rig that hasn't screwed with it (i.e. -  purposefully overclocked it without knowing what the heck they are doing :rolleyes:) will really hurt these things. :lolflag:

I think (like when you talk to auto mechanics and gunsmiths who have been in the business for long) most motherboard/CPU screw-up's you see come from computer newbees screwing around with things they just don't understand (but won't admit to it). :)

---

### Post by meindian523 on 2008-03-01
But it's always preferable to keep it as low as possible,isn't it?Why take chances?

---

### Post by meindian523 on 2008-03-01
> **herbster said:**
> It would appear your hardware isn't cooperating with the lm-sensors drivers. Acpi seems to work, so that's good-- it doesn't work for me, so there you go.

So what am I to do to find CPU temperature during runtime?

---

### Post by dcstar on 2008-03-01
> **meindian523 said:**
> So what am I to do to find CPU temperature during runtime?

Right-click the top panel, and add the Hardware Sensors Monitor by dragging it to the place you want it top be in a panel.

Then go into the preferences for it and select what you want displayed.

---

### Post by dcstar on 2008-03-01
> **RedRat said:**
> Yeah I got exactly the same value as with acpi -t. However, mine comes back with exactly "40.0 degrees C". OK, being a scientist I worry a bit about getting back a value of exactly 40.0. This value has held steady now for over 5 hours. I hope it is right.

Gee, that also is always 40C on mine, guess it must be working exactly the same on both our PCs.......      NOT!

That value is not worth the time taken looking at it, it is far better to use something that actually changes and reflects reality a little closer.......

---

### Post by herbster on 2008-03-01
I don't think the hardware sensors applet will work, isn't it based off lm sensors output? If not, well then that's what he can do.

---

### Post by maniac_X on 2008-03-01
> **meindian523 said:**
> But it's always preferable to keep it as low as possible,isn't it?Why take chances?

Yes, keeping the temp. down will ensure longer CPU lifespan. As for you not ever opening your case up, it's not as scary as you might think. And considering that you haven't opened it and been running it since '06, I would take a wild guess and suggest that you definately might have a dust bunny or three making home in your case :) 
Get yourself a can of air that they sell at your local computer suplies/office supplies store and open that case up and first thing is blow out any dust from the CPU heatsink. You might be surprised how just that single action might help lower the temp some degrees. Also check your case fan. Dust can build up on that as well. Check any grills for build up.

---

### Post by dcstar on 2008-03-02
> **herbster said:**
> I don't think the hardware sensors applet will work, isn't it based off lm sensors output? If not, well then that's what he can do.

It uses whatever is available, ACPI, lmsensors etc. etc., you decide which ones to display.

---

### Post by meindian523 on 2008-03-02
Um,hardware monitor?I'm using Ubuntu 7.04 and that has only one option by default which is CPU Frequency scaling monitor which is not possible(CPU Frequency scaling,that is) in my box according some messages on bootup.I had added another Computer Temperature Monitor by my own enterprise quite some time ago and it has the preferences for HDD Temp(which works OK,but is of no use or relevance to this topic,I always knew I could monitor my HDD temp),Kernel i2c sensors(which when selected says No thermal zones) and ACPI which is stuck at 40*C.

---

### Post by brunolabs on 2008-03-02
My Pentium 4 3.2 GHz temp goes from 40 to 50 Celsius.

---

### Post by jeffus_il on 2008-03-02
Different CPU's run at different temperatures. I have seen from 20C to 70C, but around 60C was in the old days, you could fry an egg on one. the temperatures reported are not accurate, bios, diiffers from acpi, which again is not the same the lm_sensors stuff. You can access the manufacturers sites for accurate info (Intel and Amd usually) I currently have 22C for the sensor chip I have and 31C for the acpi one. A difference of 9C. I don't really use the temperatures for absolute comparisons, only releative, that is I remember what it was when the fans were clean and the cpu-c ooler interface well greased, I use that as a base reading, and then I see if it heats up over time, also running CPU intensive applications really hots it up, so be aware of that when you read your temperature.

---

### Post by meindian523 on 2008-03-03
My box starts off at 48*C,that's much higher than the maximum ambient temperature of 37*C.

---

### Post by jeffus_il on 2008-03-03
Get you CPU model, go to the Intel site if it's Intel or same for AMD. Find the spec sheet for your CPU. Find the acceptable temperature range. If yours is within the range, happy computing, if not pop open the box, or get someone else to if it;s not within you skill range, remove the CPU fan and cooler, clean the fan, you can also replace it with a new one which may be more efficient, also make sure that you have a good layer of heat conducting grease between the aluminium cooler and the cpu. (available from your local computer shop) I do it every six months or so, if you're not a fiddler like me, take it to a technician.

---

### Post by matherians2 on 2008-03-03
Yikes, 60C could cause a hard drive failure.

---

### Post by jserink on 2008-03-03
Hi All:

The temperature of your CPU is based on 2 things:
1. The ambient termperature,
2. The load.

I live in Singapore, with air conditioning off, ambient is ~31C for most of the day. With power now on and running at the min clock and core voltage, my Turion notebook shows 53C. That is normal. Was in Korea last week, in hotel same conditions, idle was ~44C, in a server room that was like an icebox, ~40C.

The automatic ACPI trip for my machine is shown here:
jerinkturion jserink # acpitool -tv
  Thermal zone 1 : ok, 52 C
  Trip points :
  -------------
  critical (S5):           100 C
  passive:                 105 C: tc1=2 tc2=3 tsp=40 devices=0xffff81000136db10


Cheers,
John

---

### Post by RedRat on 2008-03-03
> **jeffus_il said:**
> Get you CPU model, go to the Intel site if it's Intel or same for AMD. Find the spec sheet for your CPU. Find the acceptable temperature range. If yours is within the range, happy computing, if not pop open the box, or get someone else to if it;s not within you skill range, remove the CPU fan and cooler, clean the fan, you can also replace it with a new one which may be more efficient, also ***_make sure that you have a good layer of heat conducting grease between the aluminium cooler and the cpu_***. (available from your local computer shop) I do it every six months or so, if you're not a fiddler like me, take it to a technician.

I would suggest that you read the instruction for the heat conducting grease before you apply it. Arctic Silver, the one I use, says to apply a very thin coating. Also, clean all of the old grease off the surfaces. Arctic Silver makes a kit with a cleaner solvent. My guess is that other manufacturers do the same. I made the mistake of putting too much grease on and had to go back and redo it.

---

### Post by talsemgeest on 2008-03-03
The thinnest layer of thermal grease you can get, while still filling all of the minute holes is ideal

---

### Post by jeffus_il on 2008-03-03
> **talsemgeest said:**
> The thinnest layer of thermal grease you can get, while still filling all of the minute holes is ideal
Thanks for the correction!

---

### Post by talsemgeest on 2008-03-03
No problemo. Just in case anyone wants to know, its because the thermal grease doesn't conduct as well as pure contact with the metal, but its almost impossible to get 100% contact, so thats why we have thermal grease (or paste)

---

### Post by Iam138 on 2008-03-03
Nothing like a sweet lap job and some AS5 to keep temps. down. 


 BTW 80%+ Isopropyl alcohol (rubbbing alcohol) and a coffee filter or coarse (cheap) paper towel will work fine for removing old or excess TIM, just allow a few minutes for total evaporation. Or if you want to get real hardcore about it run your CPU naked. I wouldn't advise such drastic measures if your inexperienced, shakey of hand or not an enthusiast where every drop in core temps matters.

---

### Post by jeffus_il on 2008-03-04
Well ... If we're sharing recipes ...

Make sure you have a mechanically good cooler/fan assembly, some of the older ones do not put even pressure on the aluminum/cpu interface, giving uneven contact and bad heat transfer. The newer ones connecting via drilled holes in the motherboard are preferable, and make sure the springs move freely, they help balance the pressure exerted on the four corners of the cooler.

Newbies, please ignore this nonsense, its really for "nuts". a club of which I am a card carrying member.

---

### Post by meindian523 on 2008-03-04
> **jeffus_il said:**
> Get you CPU model, go to the Intel site if it's Intel or same for AMD. Find the spec sheet for your CPU. Find the acceptable temperature range. If yours is within the range, happy computing, if not pop open the box, or get someone else to if it;s not within you skill range, remove the CPU fan and cooler, clean the fan, you can also replace it with a new one which may be more efficient, also make sure that you have a good layer of heat conducting grease between the aluminium cooler and the cpu. (available from your local computer shop) I do it every six months or so, if you're not a fiddler like me, take it to a technician.

I already did that and I posted the results up somewhere in this thread and the links were there too,so people could independently verify whether I had the correct page.
EDIT:
It's post #25.

Could all these gurus tell me what this means:
```
easwarh@l1nuxr0cks:~$ acpitool -tv
  Thermal zone 1 : ok, 40 C
  Trip points : 
  ------------- 
  critical (S5):           75 C
  passive:                 73 C: tc1=4 tc2=3 tsp=60 devices=0xda78b338 
  active[0]:               73 C: devices=0xda78bb94 

easwarh@l1nuxr0cks:~$
```

---

### Post by jeffus_il on 2008-03-04
The Intel page states a maximum case temperature of lower 60's C to high 60's for the case temperature, on different models of the Pentium D. Yours was 48C which seems to be acceptable. don't expect you temperature reading to be as low as the Dual Core readings posted here.

---

### Post by meindian523 on 2008-03-04
> **jeffus_il said:**
> The Intel page states a maximum case temperature of lower 60's C to high 60's for the case temperature, on different models of the Pentium D. Yours was 48C which seems to be acceptable. don't expect you temperature reading to be as low as the Dual Core readings posted here.

If you are referring to the post above which said thermal 1:40*C OK,you might find it interesting to read this post:
> **herbster said:**
> @meindian523,

The acpi is probably reading your motherboard temp. Try acpi -V and see the output?

and the dialog between myself and herbster about lm-sensors not working on my box.Not meant as a insult or anything,but I guess the above has some relevance here.

My processor is 2.80 GHz which if I read the Table 2 [here]("http://www.intel.com/cd/channel/reseller/asmo-na/eng/216412.htm") right is the processor number 920 which has max case temperature 62.1*C which I think has been exceeded by the 70*C I mentioned earlier,unless there's a difference between max case temperature and whatever Hardware Monitoring in the BIOS shows.

---

### Post by jeffus_il on 2008-03-04
The temperatures are not accurate as posted previously. If you machine is not crashing, you can carry on computing, if it bothers you, take the mountains of advice from the previous posts and try to lower your CPU temperature. If you are still unhappy, you can try to fiddle the bios settings lowering the CPU core voltages and searching the hardware forums for tweaks etcetera...

---

### Post by meindian523 on 2008-03-04
Which temperatures are not accurate?The ones I posted or the ones others posted?My machine does not crash regularly but does once in a long while(which is completely random,there might be two incidents in a week,then nothing for next four weeks,which I guess would be more of a problem with Xserver.)What do you say?

---

### Post by jeffus_il on 2008-03-04
The intel temperatures are of course extremely accurate, temoeratures read by the computer are not, bios, monitoring chips, lm_sensors, acpi and whatever else, as I mentioned previously, I prefer to look at relative temperatures over time, not absolute on the spot measurements.

---

### Post by meindian523 on 2008-03-05
Ohk.

---

### Post by MikeJ112 on 2008-03-05
Is there such a thing as a PC running too cool then? Mine nevers seems to go above 34c . Im running an AMD64 2.4x2 Dual Core in quite a small case. I've taken the readings from my BIOS

---

### Post by meindian523 on 2008-03-05
IMHO and AFAIK,no.Just be happy that your fans are working well and doing their job.

---

### Post by herbster on 2008-03-05
Meindian523, what kind of cooling do you have in your case? Do you have any case fans at all?

---

### Post by talsemgeest on 2008-03-05
The cooler your pc, the longer it is going to last. Thats why I have 6 fans in my case

---

### Post by jseiser on 2008-03-05
> **motion parallax said:**
> I've been having similar issues.  My laptop runs around 54 C at max performance.  Been scaring me a little, so I bought one of those chill pads.  Targus Tornado.  Seated on my lap, the temp came down to 31 C.  I returned it for a Belkin (mostly curious) and now the temp stays around 48 C.  I'm getting the Targus back.

I use one of these with my laptops, not to keep the laptop cool, but to keep my damn legs from burning up after a few minutes :)  I  have a low end 'green' via chipset, and it still runs hot.

---

### Post by Butthead on 2008-03-05
> **talsemgeest said:**
> The cooler your pc, the longer it is going to last. Thats why I have 6 fans in my case

Just think about how much heat insulating dust you're sucking into that thing. :lolflag:

Poorly quoting the rock group Queen here: "Who wants (a PC) to live forever?" :)

---

### Post by talsemgeest on 2008-03-05
> **Butthead said:**
> Just think about how much heat insulating dust you're sucking into that thing. :lolflag:

Poorly quoting the rock group Queen here: "Who wants (a PC) to live forever?" :)
No dust. Got good dust filters by each one. And only three of four are on the outside

---

### Post by herbster on 2008-03-05
Damn undercover Intel sales reps wanting us to kill our CPUs :roll: :D

---

### Post by meindian523 on 2008-03-06
@herbster

1 fan on the SMPS,1 on the case,at the least,that what I can make out without opening the case.

---

### Post by Butthead on 2008-03-06
> **herbster said:**
> Damn undercover Intel sales reps wanting us to kill our CPUs :roll: :D

Hey, we gotta eat sometimes too. :) 

And um, buy AMD. :lolflag:

---

### Post by Dr.Ninethousand on 2008-03-08
I've installed, configured and reconfigured lm-sensors, but KSensors and KDE System Guard always show an idle temp of around 11C.  

When running large applications or stress testing with cpuburn-in, the temp never goes above 36C.

Obviously these can't be correct..  can they?.

Also there is no thermal zone content anywhere in my system, and none of those methods work..

it's a fairly new MSI box, I assume there are decent sensors in it, but all I've got working is my core temps (which appear to be wrong) and HDD temps, which is functioning normally afaik..  

also BIOS reports a fairly normal 35C..

:confused:

---

