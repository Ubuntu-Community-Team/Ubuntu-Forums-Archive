---
title: "virtual box error."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Nedux on 2007-10-25
hi there ` I`m trint to start a virtual machine that I set up on virtual box and i get this error 

Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

please help ,

---

### Post by pana.corbului on 2007-12-30
try ```
sudo chgrp vboxusers /dev/net/tun
sudo chmod 660 /dev/net/tun
```

---

