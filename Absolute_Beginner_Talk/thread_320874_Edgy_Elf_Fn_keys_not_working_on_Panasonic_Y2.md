---
title: "Edgy Elf Fn keys not working on Panasonic Y2"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by malefactor on 2006-12-18
After installing Edgy Elf my Fn keys no longer work, I know they have worked in previous versions of ubuntu but they no longer work in Edgy. 

After doing some searching I found a guide for fixing this problem, but its slightly over my head because i dont have very much experience with ubuntu other then using apt-get and using basic programs like VLC and Firefox. 

Guide: [http://www.da-cha.org/letsnote/](http://www.da-cha.org/letsnote/)

I have a Y2, my kernel is version 2.6, i believe i meet the system requirements.

I tryed option 1 "Instructions by driver package" but when i get to the command "sudo modprobe pcc_acpi" i get an error....

"FATAL: Error inserting pcc_acpi (/lib/modules/2.6.17-10-generic/kernel/drivers/acpi/pcc_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)"

I looked at option 2 but it involved building and installing the kernel, which seemed harder and even more over my head.

Can some one please make the directions more "new user friendly" or try to tell me what iv done wrong? If you have any questions about how i followed the directions just ask, Im not sure which step i messed up.

thanks guys :mrgreen:

---

### Post by malefactor on 2006-12-18
bump.

If anyone knows a better way to fix Fn keys on a panasonic y2 toughbook please let me know.

---

### Post by malefactor on 2006-12-18
one more bump before bed. 

if anyone has any advice were i could go for help on doing this it would be very appreciated. Google and wikipedia just arnt getting the job done  this time. :(

---

### Post by malefactor on 2006-12-19
bump. 

tried it again and im still getting the same result. Im not sure if this just doesn't work or if im doing some thing wrong.

im fairly sure its this part "You will need to download a driver package. It is now only support 2.6 series kernel. **You'll also need a script to handle the hotkey events**."

I downloaded and untared the hotkey handlers but im not really sure what im supposed to be doing with them? :confused: 

if anyone has any suggestions to help me relive my ](*,)  it would be most appreciated

---

### Post by malefactor on 2006-12-19
bump. last time :( 

i cant seem to get any help from anyone, i have pritty much given up on doing things like fixing my touchpad (circular scroling) and adjusting my brightness or volume (without a slider) or running at my regular resolution. Iv moved on to setting up my programs, which is going as smoothly as everything else i try.

dvd's wont play, esayubuntu can find stuff and wont work right, automatix says its 404ing, and i dont even wana think about how hard its going to get mathematica to run on this thing

i guess ill give it a few more days, but iv really hit some big walls, maybe my hardware is just to unique

still waiting for help on how to use this manual to adjust brightness on a y2

---

### Post by idlewild on 2006-12-20
Panasonic laptops are not that popular, it seems particularly true when you look at linux development. However you should be able to get everything to work, but linux support for them (on this forum for example) will be pretty poor.

Do you have the default edgy kernel? What version of pcc-acpi did you download? What is the output of make and make install?

You don't need to worry about scripts, ubuntu has working ones already installed.

---

