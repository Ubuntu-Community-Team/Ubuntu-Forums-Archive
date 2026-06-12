---
title: "What are the yaboot.conf Splash options?  Quiet, and what else?"
date: 2007-10-26
forum: Apple PPC Users
---

### Post by magnolia fan on 2007-10-26
Can anyone tell me what the alternatives to append = quiet splash are in the the yaboot.conf file?  I would like to see a partial scroll of the boot lines as well as the Ubuntu graphic.

--thanks

---

### Post by BladeMelbourne on 2007-10-26
These are the options that I know about...
append="video=ofonly nosplash single"

The ofonly is required on some Macs (like the G4 Mac Mini).
Single boots to the command line (GDM / X doesn't start automatically).
Nosplash is straight forward.

---

