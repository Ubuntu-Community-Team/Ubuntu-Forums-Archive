---
title: "CPU Temperature"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by trebor7_1 on 2007-01-26
Totally new and looking for advice.
Just loaded Ubuntu 6.06 last night and have most things working.
Would like to see CPU temp fan speed etc.
Loaded GKrellM which seems ok however trying to set that up lead to no sensors detected.
Loaded xmbmon but now totally stuck.
Cannot do anything with mbmon most I've done is find it in usr/bin.
Permissions tell me its owned by root so I suppose thats why I cannot run it ???
What next any help would be great, thanks.
:confused:

---

### Post by energiya on 2007-01-26
Try [lm-sensors]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29").  If you want this info without terminal you can use conky in association with lm-sensors.

---

### Post by ComplexNumber on 2007-01-26
install lm_sensors. if that doesn't work, fire up synaptic and do a keyword search on 'name and description' for "cpu sensor"(without the quotes) or "sensor". have a look through the summary to see if there is anything else relevant.

---

