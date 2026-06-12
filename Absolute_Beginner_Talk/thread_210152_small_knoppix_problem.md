---
title: "small knoppix problem"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-07-06
I know this is not a knoppix forum, but the live CD tells me that it could not find the knoppix filesystem, how can i correct that?

---

### Post by taurus on 2006-07-06
How did you burn the ISO image and before you did any burning, did you run checksum (md5sum) to check the integrity of the file?

---

### Post by dmizer on 2006-07-06
i'll also add ... at what speed did you burn knoppix?  have you tried any boot switches like noacpi ...

---

### Post by Somenoob on 2006-07-06
It was quite a while ago when i burned it, i do no remember the speed, but i have tried the same disk on other machines it worked well then.

---

### Post by dmizer on 2006-07-06
then your best bet is going to be to try some boot switches.  start with noapic acpi=off you can check for more options here: [http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt)

---

