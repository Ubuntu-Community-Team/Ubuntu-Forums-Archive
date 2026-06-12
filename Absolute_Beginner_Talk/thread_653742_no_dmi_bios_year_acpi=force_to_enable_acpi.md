---
title: "no dmi bios year acpi=force to enable acpi"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by euwinn on 2007-12-30
I have a cd version 7.10 ubuntu and in attempting to install, I get the message "no dmi bios year acpi= force is required to enable acpi". I have been running win98se on my computers. Is there a simple fix for this or could someone direct me to some documentation concerning this?

---

### Post by nonewmsgs on 2007-12-30
iirc this just means that some of the powersave features aren't going to run because basically your computer might not be new enough to properly take advantage of them.  this shouldn't be an error keeping you from installing.

---

### Post by euwinn on 2007-12-30
Thank you for the info. I do get the ubuntu screen with the band moving back and forth, but that is all that happens when I invoke "install". The "verify cd" works, the memory test works, but the install does nothing except have the band move back and forth.

---

### Post by Neovos on 2008-02-11
initially it looks like your bios might not have acpi support (it might want the older version "apm" which is another module alltogether) but the fact that it's telling you to force acpi might give you another thing to try. 

when you get to your startup screen on the list, try adding "acpi=force" to the startup options below before you boot it up. That is how you "force" it to run which might get it working. Here are some other boot options that might be of use. They just fixed a problem I had with acpi interupts. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by swoody on 2008-06-24
I'm having the exact same problem on my Windows 98 comp. Has anyone figured out a soloution? My comp's running an 8gb IDE harddrive, Pentium II, and 96mb RAM. I know the install disc is good since I used it to install Hardy on my laptop.

I tried acpi=force, noacpi, and acpi=off, but it's not working. When I try acpi=force, it still gives me the same error message, when I try noacpi or acpi=off it'll start the bootsplash, but will wind up freezing with the lights on my keyboard flashing.

Any advice would be greatly apppreciated! Thank you all.

---

