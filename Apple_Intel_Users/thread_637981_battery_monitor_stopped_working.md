---
title: "battery monitor stopped working"
date: 2007-12-11
forum: Apple Intel Users
---

### Post by trevelyn on 2007-12-11
acpi -V gives me:

root@celeritas:/home/trevelyn# acpi -V
     Battery 1: charging, 0%, charging at zero rate - will never fully charge.
No support for device type: thermal
  AC Adapter 1: on-line
root@celeritas:/home/trevelyn# 

any ideas??  i search google and the forums and can't find a single solution.

root@celeritas:/home/trevelyn# cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mW
remaining capacity:      0 mWh
present voltage:         0 mV
root@celeritas:/home/trevelyn# cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         0 mWh
last full capacity:      0 mWh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            
OEM info:                
root@celeritas:/home/trevelyn# ???

---

### Post by trevelyn on 2007-12-11
yeah, so while the machine was on and running i took out the battery.  (and it shut off)  I plugged it back into the machine, and booted it back up and *poof!* the battery monitor works again! :confused: :confused:

root@celeritas:/home/trevelyn# cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            19711 mW
remaining capacity:      50080 mWh
present voltage:         12115 mV

root@celeritas:/home/trevelyn# cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         50200 mWh
last full capacity:      53790 mWh
battery technology:      rechargeable
design voltage:          10950 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            ASMB013
serial number:           
battery type:            LION013
OEM info:                DPON013
root@celeritas:/home/trevelyn# 

:confused: sorry, if this happens to anyone take the battery out (while running on battery) and reinsert it, and boot back up. - trev.

---

### Post by cyberdork33 on 2007-12-11
my guess is that you reset the SMC controller.

---

### Post by trevelyn on 2007-12-11
is there any way to do that without my archaic method? 

would modprobe applesmc help?

thanks - Trev

---

### Post by cyberdork33 on 2007-12-11
no the smc controller is hardware...

there are instructions for resetting it on Apple's website, which pretty much says to take the battery out and unplug it...

[http://docs.info.apple.com/article.html?artnum=303319](http://docs.info.apple.com/article.html?artnum=303319)

---

