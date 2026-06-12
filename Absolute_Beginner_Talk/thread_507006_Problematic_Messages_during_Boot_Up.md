---
title: "Problematic Messages during Boot Up"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by gautam_icykool on 2007-07-22
Hi guys i have this prob in ubuntu.. I have an AMD Turion 64x2 duo core processor.. I downloaded ubuntu 7.04 a few days back (32 bit version only)

guys during the boot up process of ubuntu, i get a lot of messages that are kinda freaking me out... its like as follows:
First of all as soon as i select ubuntu from the grub loader, i get a message
Starting Up:
MP-BIOS bug : 8254 Timer not connected ......( something more )

Then the booting starts... i get a lot of messages like:

Loading Hardware drivers:

firmware_helper (3819) : main : error loading '/li b/firmware/bcm4xx_microcode5.fw' for device '/class/firmware/0000:30:00.0' with driver '(unknown)'

i get this three or four times and then a hard disk cluster scan starts where i get more of the same message.

After that i get a lot of [OK] against a no. of things... because of this my boot up takes about 50-60 seconds which i think is too long...

Any suggestions !!!!!!!!!!!!!! Thanks in advance !!! Sorry if its been posted before

---

### Post by e_james on 2007-07-23
I don't have much experience of linux / ubuntu but startup error messages aren't necessarily a big issue. Sometimes it's just a way to establish that a particular facility is not available. After the boot sequence has completed, if something doesn't work which you want to work, then the error messages may tell you why. I think that MP-BIOS message might be the one that means your ACPI won't work properly. This affects suspend and hibernate facilities. If you search these forums it should become noticeable that this is one of the outstanding issues between linux users and motherboard manufacturers, especially for laptops.

---

