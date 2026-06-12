---
title: "[lm-sensors] No sensors found!"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2007-07-15
Hi. I upgraded my PC and I want to be able to do a very basic thing, that is to monitor the CPU and motherboard temperature. 

Here are my specs:

Motherboard: Asus P5L-VM 1394
CPU: Intel Duo Core2 @ 1.86 GHz
RAM: DDR2 1024 MB @ 800 MHz (but working @ 667 MHz because of the MB) (OCZ)
Video: integrated chip on MB (Intel 945)

Now, I followed the HowTo on [ubuntuguide](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29) and the one on [doc.gwos.org](http://doc.gwos.org/index.php/Lm-sensors_hddtemp), to no avail.

Here's what happens: when I 

```
# sensors-detect
```

and choose the default answer to all of the questions I get there, I get the following modules:

```

# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
w83627ehf

```

The modules are properly inserted in /etc/modules (I saw somewhere that it was recommended to add them in reverse order, and I also tried that too), and then I 

```

# modprobe i2c-i801
# modprobe eeprom
# modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.20-16-generic/kernel/drivers/hwmon/w83627ehf.ko): No such device

``` 

...although it appears under /lib/modules/2.6.20-16-generic/kernel/drivers/hwmon ...

and here's the final step:

```

# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

What can I do ?... :???: 

Since I'm a KDE user, I don't want to have the temperature applet installed, I just want to be able to run sensors and parse the output in a script that will alert me whenever something is not right.

I'd appreciate any help, if you happen to know a way to fix this. :-)



**EDIT** I just remembered. When I upgraded my PC, I should have mentioned that I only bought a new motherboard, a new CPU, the RAM and the case+power supply and put them up myself, by *keeping* the old HDD - and thus keeping the old Ubuntu install. Is this important, I mean it was the 32bit i386 version, the "normal" one... ?!

---

### Post by forestpixie on 2007-07-15
I couldn't get that to run either when I followed the guide and I had a FATAL.

When I had to do a reinstall I apt-got lmsensors, completely forgot about the script business in the wiki and when I ran sensors-detect it worked :o

Not sure whether it'll do that for you -

---

### Post by LLRNR on 2007-07-15
Forestpixie, thanks for the reply. Let me see, do I get this clear, you mean after the Ubuntu full reinstall you got it to work without a clinch on the fresh system? 

That's a good idea I think... by the way. Is everything OK if I still use the 32bit version now that I've got a 64bit CPU?

---

### Post by crimesaucer on 2007-07-15
Try this for temp in your Terminal:

```
acpi -V
```


...also, try to install Conky: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)


There is also a panel plug-in that monitors CPU, MEM, and SWAP...and another panel plug-in that has a CPU graph.

---

### Post by LLRNR on 2007-07-15
For acpi -V:

```
# acpi -V
No support for device type: thermal
```

As for conky, I followed the short and easy way. I got the .conkyrc with

```
$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

And here's the [screenshot](http://img120.imageshack.us/img120/5605/conkyrm5.png) I made.

It doesn't seem to show temperature stuff... Why do I think that even if it did, it would have had to read it in the first place from the *sensors* output? The widgets in the Karamba/Superkaramba set work this way too if I'm not mistaking.

Thanks for your answers.

---

### Post by crimesaucer on 2007-07-15
Here is the list of Variables to write into your .conkyrc to show temp: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Here is a list of Settings to customize the way it looks: [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Here is a good page of examples and .conkyrc files to download and use: [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)


This is what mine looks like (showing temp): [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22a.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22a.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22a-1.png[/IMG]

---

### Post by crimesaucer on 2007-07-15
I'm not too sure, but you might want to use this Variable for your temp??:

```

adt746xcpu 		 CPU temperature from therm_adt746x
adt746xfan 		Fan speed from therm_adt746x

```


My computer use ACPI so this works for me. 

```
acpitemp         ACPI temperature in C.
```


....so that's why the command acpi -V works for me:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22y-1.png[/IMG]

---

### Post by bodhi.zazen on 2007-07-15
This is an awesome post on getting sensors working :

[http://ubuntuforums.org/showpost.php?&p=2468147&postcount=24](http://ubuntuforums.org/showpost.php?&p=2468147&postcount=24)

[color=blue]Thank's ayenack [/color]

once lm-sensors is installed and configured you can display temp with conky, gkrellm, .... panel applet, xsensors, you pick ;)

---

### Post by crimesaucer on 2007-07-15
> **bodhi.zazen said:**
> This is an awesome post on getting sensors working :

[http://ubuntuforums.org/showpost.php?&p=2468147&postcount=24](http://ubuntuforums.org/showpost.php?&p=2468147&postcount=24)

[color=blue]Thank's ayenack [/color]

once lm-sensors is installed and configured you can display temp with conky, gkrellm, .... panel applet, xsensors, you pick ;)

Not everyone can use lm-sensors...I'm one of the people that can't since I have a cheap laptop. (The Mobile Intel 910GML Express chipset is optimized for the Intel Celeron M processor.)


Save yourself the time and find out if your computer can use lm-sensors: [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

---

### Post by LLRNR on 2007-07-15
bodhi: The post on getting lm-sensors to work is what I did, in a way or another. And after following the steps described there, I still get "no sensors detected".

About the .conkyrc file. I tried several versions but each one was looking for a certain temp_1 / temp_2 thing under /sys/bus/i2c/devices. And there wasn't anything there that "sounded" like temp_1 or 2.

I went through the list of devices on lm-sensors.org. Apparently I'm using

```

Intel 	 82801G (ICH7) 	 yes 	 i2c-i801 	 2.9.0 	 2.6.11

```

which doesn't have any additional info... so it *should* work :-S

I'm not sure on what's wrong. I think I'll try more for another day or two and if I can't get it straight I'll try a reinstall, all my important stuff are backup-ed anyway.

In any case, thanks for your help. I'll keep you posted when I find something new.

---

### Post by crimesaucer on 2007-07-15
This might be a thread where you can ask questions at: [http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

and this was the wiki: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)


...you can ask questions about your .conkyrc over here: [http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky)


someone will help you customize your .conkyrc for your computer.

---

### Post by forestpixie on 2007-07-15
> **LLRNR said:**
> Forestpixie, thanks for the reply. Let me see, do I get this clear, you mean after the Ubuntu full reinstall you got it to work without a clinch on the fresh system? 

That's a good idea I think... by the way. Is everything OK if I still use the 32bit version now that I've got a 64bit CPU?

Hi - yes didn't have a problem with it. Certainly didn't need to do all this :)
guess I was lucky at the time

Hope it's working for you now

---

