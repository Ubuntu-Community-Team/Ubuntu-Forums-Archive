---
title: "Seft-made script doesn't work right when scheduled"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Limulf on 2007-11-16
Hello. I have written this tiny script, called "Disco.sh" so I can keep an eye on my hard disk's temperature and number of cycles:```
date >> /home/thorin/Configuración/Vigilancia.log
smartctl -d ata -a /dev/sda | grep Load_Cycle_Count >> /home/thorin/Configuración/Vigilancia.log
smartctl -d ata -a /dev/sda | grep Temperature_Celsius >> /home/thorin/Configuración/Vigilancia.log
``` It needs superuser privileges, so if I invoke it from a root terminal ("gksu /usr/bin/x-terminal-emulator", then "/home/thorin/.scripts/Disco.sh"), it works flawlessly. Three lines appear in the file "Vigilancia.log": one for date, another one for total "Load_Cycle_Count", and the last one prints hard disk's temperature.

 I want this script to be automatically run each hour, so I execute "gksudo /usr/bin/gnome-schedule", and add a new task to be done each hour: "/home/thorin/.scripts/Disco.sh". My problem is that each hour, only the date gets added to the file "Vigilancia.log", not the cycle nor temperature. Where am I blundering? Thanks for your time reading this. :-)

(Sorry about the typo in the post's topic, I can't change it) :oops:

---

### Post by oilchangeguy on 2007-11-16
why not use hddtemp? it's available from synaptic. works if your hd has s.m.a.r.t.

---

### Post by Limulf on 2007-11-16
@oilchangeguy : Many thanks for your quick and useful answer. Reading the man file of "hddtemp" I have found that with "sudo hddtemp /dev/sda -d" I can see hard disk's temperature from Gnome's panel through "sensors-applet". \\:D/

 About the other command I needed, I googled a bit about "grep" and put together this new one-line script, which I thought would work:```
smartctl -d ata -a /dev/sda | grep "Local Time\|Load_Cycle" >> /home/thorin/Configuración/Vigilancia.log
``` Regretfully, it still wouldn't. Finally, more to cover another possibility than from any conviction that it had any chance to work, I tried this last script:```
sudo smartctl -d ata -a /dev/sda | grep "Local Time\|Load_Cycle" >> /home/thorin/Configuración/Vigilancia.log
``` To my surprise, it performs perfectly, it is executed once every hour.

 I think (please someone correct me if I am chasing moonbeams here) that my error was thinking about the Gnome Scheduler with superuser privileges as a root terminal, where all commands are run as root. Instead, it only grants root power to those commands you prefix with "sudo", without asking for the password.

 Best regards.

---

