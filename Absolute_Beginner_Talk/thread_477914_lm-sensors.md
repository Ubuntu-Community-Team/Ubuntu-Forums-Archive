---
title: "lm-sensors"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by AriciU on 2007-06-18
I've installed lm-sensors and configured it without any problems.

It is possible to modify the output of the command "sensors | grep CPU Temp" from the default "CPU Temp: +32°C (low = +127°C, high = +127°C) sensor = thermistor" to just "CPU Temp: 32°C". Without the "+" and the "(low = +127°C, high = +127°C) sensor = thermistor" after the value.

If it's possible then what and where do i have to edit?

Thanks

---

### Post by webdr on 2007-06-18
JAG (Just a Guess) sensor.conf

---

### Post by AriciU on 2007-06-18
Can't find anything about it in sensors.conf. It's probably some code i can't recognise i guess...

---

### Post by 5-HT on 2007-06-18
Can be done by piping the output of sensors through cut. As an example:
I have the following in my .conkyrc
```
$alignc${color red} CPU Temps(C): $color ${execi 6 /usr/bin/sensors | grep temp | paste -s | cut -c33-34,37-38,109-110}
``` that cuts 
```
coretemp-isa-0000
Adapter: ISA adapter
temp1:       +34°C  (high =  +100°C)                     

coretemp-isa-0001
Adapter: ISA adapter
temp1:       +33°C  (high =  +100°C) 
```Into
```
34  33 
```and adds some formatting to it
[quote=actual command] /usr/bin/sensors | grep temp | paste -s | cut -c33-34,37-38,109-110[/quote]You'll need to play around with characters you want cut for your specific case (please refer to 'man cut' for more information) and the paste pipe won't be necessary in your case. Once you get the proper command, you can make an alias for it and export it in your .bashrc so that something like 'temp' will run that command (please refer to 'man alias' for information on aliases if you are unfamiliar with them).

cheers,

---

### Post by AriciU on 2007-06-18
Got it working. Thanks! :)

Another thing. I entered the alias in the ~/.bashrc file but it says command not found when i'm trying to use it. Do i have to reboot the system for it to take effect or can i just reload the .bashrc file?

---

### Post by 5-HT on 2007-06-18
> **AriciU said:**
> Got it working. Thanks! :)

Another thing. I entered the alias in the ~/.bashrc file but it says command not found when i'm trying to use it. Do i have to reboot the system for it to take effect or can i just reload the .bashrc file?

Glad you got it working. :p Yup, you can just source .bashrc or open up another shell instead of rebooting ```

. ~/.bashrc
```

---

### Post by AriciU on 2007-06-18
Works :) I forgot to put the ' after =

---

