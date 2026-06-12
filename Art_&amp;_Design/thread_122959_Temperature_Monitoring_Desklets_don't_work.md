---
title: "Temperature Monitoring Desklets don't work"
date: 2006-01-28
forum: Art &amp; Design
---

### Post by Piggah on 2006-01-28
Hi,

Well, simple problem really. Any of the system temperature monitoring desklets don't seem to work. They all display 0C. (Would be nice if it were true. :P ) I was just wondering if I need to have something else installed for them to work. I really need some sort of temperature monitoring device for ubuntu, and desklets seem like the only thing right now. 

Thanks in advance. :)

---

### Post by bernardfrancois on 2006-01-29
Make sure you have the acpi package installed.

If you have, you can check the contents of the files in */proc/acpi* (there's a folder *thermal_zone* over there, probably the contents are in one of those files.

If you're not such a console admirer (or you want to see it fast if the temperature's there, open up a console (ALT+F2 xterm) and paste this:

```

for i in $(find /proc/acpi) ; do [ -r "$i" ] && [ -f "$i" ] && { echo -e "\n\n$i\n------------\n\n"; cat $i ; } ; done

```

Here it doesn't work. It worked with my previous motherboard though. It depends on the sensors on the motherboard, they aren't always recognised. Probably updating your motherboard's firmware might help if it doesn't work.

---

