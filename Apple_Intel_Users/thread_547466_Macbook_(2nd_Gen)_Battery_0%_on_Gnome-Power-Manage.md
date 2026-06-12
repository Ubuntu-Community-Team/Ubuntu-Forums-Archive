---
title: "Macbook (2nd Gen): Battery 0% on Gnome-Power-Management"
date: 2007-09-10
forum: Apple Intel Users
---

### Post by Jaymo on 2007-09-10
This issue seems to have just appeared out of nowhere, as I did not modify anything.
I am running Feisty on a custom 2.6.22 kernel with the mactel patch, I've been running this custom kernel for quite some time and there haven't been any issues until now.

My battery status appears as 0%, despite it being charged. I have rebooted the system, however the status remains the same.

Anyone had similar issues? My searches have largely been fruitless

When I do
cat /proc/acpi/events 
I get:
cat: event: Device or resource busy

---

### Post by Tribe on 2007-09-10
[http://ubuntuforums.org/showthread.php?t=502674](http://ubuntuforums.org/showthread.php?t=502674)

---

### Post by Jaymo on 2007-09-10
Thanks for that :). All fixed now.

---

