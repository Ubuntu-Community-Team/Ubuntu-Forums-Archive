---
title: "Asus M5A87 with Athlon II X2 250: no sensors..."
date: 2011-08-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pacha_muc on 2011-08-31
hy @ll,
 
i´m new owner of the Asus M5A87 with a Athlon II X2 250 on ubuntu natty. 
I ran the sensors-detect - do answering all questions with 'yes' an after this - the only thing sensors will show me afer reboot is:
 
[PHP]
 
medienserver2@medienserver2:~$ sensorsk10temp-pci-00c3Adapter: PCI adaptertemp1:       +38.8°C  (high = +70.0°C, crit = +70.0°C)
[/PHP]
 
and... pwmconfig will not work also... - i look via google to find a solution, but i only found threads dated 2009 or older... - so, please - can somebody can give me a short push...
 
regards,
 
Peter

---

### Post by pacha_muc on 2011-09-06
as i found out in the meantime is, that i removed 

acpi_enforce_resources=lax

from grub. Then the sensors were detect and i can see the temperatures.

But now, pwmconfig replys me with:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed 

is there a workaround for this problem?

---

