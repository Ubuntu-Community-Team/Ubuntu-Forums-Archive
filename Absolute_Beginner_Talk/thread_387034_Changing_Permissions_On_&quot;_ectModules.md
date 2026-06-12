---
title: "Changing Permissions On &quot; /ect/Modules"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by b0wlman on 2007-03-17
well im trying to follow a guide on installing my g-card driver's and i have to put in a new line. into the /ect/modules file. however everytime i open it up and edit it. i cannot save. as it's read only. i right click file /properties/permission. however i cannot click any of the options to allow me to change the permissions
please help

peace

---

### Post by cbudden on 2007-03-17
> **b0wlman said:**
> well im trying to follow a guide on installing my g-card driver's and i have to put in a new line. into the /ect/modules file. however everytime i open it up and edit it. i cannot save. as it's read only. i right click file /properties/permission. however i cannot click any of the options to allow me to change the permissions
please help

peace

Open it from the command line (Applications-Accessories-Terminal), by typing

[code]
gksudo gedit /etc/modules
[code]

---

