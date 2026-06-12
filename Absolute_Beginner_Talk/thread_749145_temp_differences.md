---
title: "temp differences?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by meniscus on 2008-04-08
Whats the difference between the temperatures invoked by the 2 following commands?

```
Acpi -t
```

and 


```
sensors
```

The CPU temp given by acpi -t always seems to be 1-2 degrees lower then the CPU temp value given by lm sensors.

Which is more accurate?

---

### Post by kpkeerthi on 2008-04-08
I would check the temperature reported in my BIOS and compare it with ACPI's and lm-sensors's.

---

### Post by mcduck on 2008-04-08
temps reported by acpi are most likely the correct ones. In many cases lm-sensors requires you to edit it's configuration file to map the sensors to right values calculate the correct readings.

---

### Post by herbster on 2008-04-08
> **kpkeerthi said:**
> I would check the temperature reported in my BIOS and compare it with ACPI's and lm-sensors's.

Yep, and I would take lm-sensors over acpi. It has always been dead-on accurate with every machine I've installed it on.

---

