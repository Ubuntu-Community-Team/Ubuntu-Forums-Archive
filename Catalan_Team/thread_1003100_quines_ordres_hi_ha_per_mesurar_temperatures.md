---
title: "quines ordres hi ha per mesurar temperatures?"
date: 2008-12-05
forum: Catalan Team
---

### Post by jinglada on 2008-12-05
em vull comprar un refrigerador per al portàtil i he llegit a
[http://foro.noticias3d.com/vbulletin/showthread.php?t=34679#4](http://foro.noticias3d.com/vbulletin/showthread.php?t=34679#4)
que mesuren les temperatures de cpu, gpu,hd, i ram.

He d'istal·lar el sensord amb el synaptic?

Si teniu alguna experiència en refrigeradors també s'agrairà.
Salutacions, Joan

---

### Post by jaume69 on 2008-12-06
Pots probar **[sensors-applet]("http://packages.ubuntu.com/intrepid/gnome/sensors-applet")** (Intrepid) desde Synaptic i mirar les dependéncies que te.
Jo només instal.lant el paquet esmentat en faig prou.
No sé si era a Gutsy o Hardy que per a tenir també la temp. del **HD** tenia que instal.lar **HDDtemp**

---

### Post by quitus on 2008-12-07
sudo apt-get install lm-sensors

sensors-detect

Contestes la opció per defecte excepte en l'ultim cas, en que automàticament et t'afegirà unes línies en l'arxiu edit /etc/modules.

Si et detecta els sensors del teu ordinador els podràs visualitzar. Com a nota haig d'afegir que no sempre es correspon amb la mesura que pots visualitzar en la bios, però et permetrà controlar el augments i seleccionar el limit en que vols que salti l'alarma.

salut

---

### Post by jinglada on 2008-12-08
> **jaume69 said:**
> Pots probar **[sensors-applet]("http://packages.ubuntu.com/intrepid/gnome/sensors-applet")** (Intrepid) desde Synaptic i mirar les dependéncies que te.
Jo només instal.lant el paquet esmentat en faig prou.
No sé si era a Gutsy o Hardy que per a tenir també la temp. del **HD** tenia que instal.lar **HDDtemp**

Un cop instal·lats quina instrucció cal donar? Com es miren les dependències?

---

### Post by jaume69 on 2008-12-08
> Un cop instal·lats quina instrucció cal donar? Com es miren les dependències? 

En la Cónsola no sé si es pot executar,no ho he mirat mai.
Jo l´únic que faig és Clik secundari,**Afegir**, a la barra on vull tenir els **Sensors** i ja està.
Després els pots configurar al teu gust,també fent Clik secundari als **Sensors**.
Jo deia lo de les dependències per si no et surt el sensor de HD,si veus alguna dependència que digui **HD**,l´instal.les.(Però crec que en Intrepid,no cal)

El que no mesura aquest Applet és el **ventilador**,velocitat,temp.

---

### Post by jinglada on 2008-12-09
> **jaume69 said:**
> Jo l´únic que faig és Clik secundari,Afegir, a la barra on vull tenir els Sensors

Quan faig "Afegir" a la barra apareix la frase "No sensors found!". Verifico que estigui instal·lat el sensors-applet i ho està amb la versió 2.2.1-1ubuntu, segons synaptic.

---

### Post by jinglada on 2008-12-09
> **quitus said:**
> sudo apt-get install lm-sensors

sensors-detect

Contestes la opció per defecte excepte en l'ultim cas, en que automàticament et t'afegirà unes línies en l'arxiu edit /etc/modules.

Si et detecta els sensors del teu ordinador els podràs visualitzar. Com a nota haig d'afegir que no sempre es correspon amb la mesura que pots visualitzar en la bios, però et permetrà controlar el augments i seleccionar el limit en que vols que salti l'alarma.

salut

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
joan@joan-laptop:~$ 

Bé, ara com sé si els detecta i què he de fer per visualitzar-los?

---

### Post by jaume69 on 2008-12-09
Que no tinguis algún problema de compatibilitat,a mi a vegades quan engego el portàtil em diu un error que ara no recordo,però després es posa bé. ¿...?

Si poso al terminal:**sensors**
Em dona la temperatura de **CPU1** i **CPU2**.

Si poso:**sensors-detect**
En fa una série de preguntes per buscar i testejar i li vaig diguen que si i al final em surt el mateix que a tu.

A reveure.

---

### Post by jinglada on 2008-12-09
He reiniciat i a la barra hi apareixen dues temperatures. Posant el ratolí al damunt apareix la informació "Core 0" en un i "Core 1" en l'altre i les temperatures quan arriben a 35º s'engega el ventilador i llavors baixa fins 31º
No sé com corresponen a cpu, gpu,hd, i ram que vaig veure al missatge citat al primer post.

---

### Post by Tomàs M. on 2008-12-09
A veure si et serveix [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29) i després "afegir al quadre - hardware sensors monitor"; jo hi tinc temperatures i velocitats de ventiladors i també s'hi poden afegir voltatges i no sé si més coses.

---

### Post by CarlesOriol on 2008-12-09
o amb comandes simples:

cat /proc/acpi/thermal_zone/THRM/temperature

---

### Post by jinglada on 2008-12-10
> **Tomàs M. said:**
> A veure si et serveix [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29) i després "afegir al quadre - hardware sensors monitor"; jo hi tinc temperatures i velocitats de ventiladors i també s'hi poden afegir voltatges i no sé si més coses.


Sembla ser que no tinc tots els sensors que cal segons el que ve a continuació. Avui he d'anar a la botiga on vaig comprar-lo per dir-los els problemes que he trobat. He de reclamar alguna cosa sobre sensors?

joan@joan-laptop:/media/disk/ubuntu$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES       
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1c00 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)YES
joan@joan-laptop:/media/disk/ubuntu$ sudo /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
joan@joan-laptop:/media/disk/ubuntu$ sudo sensors -s
joan@joan-laptop:/media/disk/ubuntu$ sudo sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +31.0°C  (high = +100.0°C, crit = +100.0°C)  

joan@joan-laptop:/media/disk/ubuntu$ 

------------------------------------------
He seguit fins al final i he instal·lat el GKrellM i tinc molta informació, sense sensor del ventilador i no sé si hi manquen més coses.

---

### Post by jinglada on 2008-12-10
> **CarlesOriol said:**
> o amb comandes simples:

cat /proc/acpi/thermal_zone/THRM/temperature

Tinc el directori però no tinc el fitxer:

joan@joan-laptop:/media/disk/ubuntu$ cat /proc/acpi/thermal_zone/THRM/temperature
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
joan@joan-laptop:/media/disk/ubuntu$ 

joan@joan-laptop:/proc/acpi/thermal_zone$ ls -l
total 0
joan@joan-laptop:/proc/acpi/thermal_zone$

---

