---
title: "Enabling / Disabling Firmware On Bootup or Shutdown"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by darKStorm on 2008-02-23
Is there a way so that when I turn on my PC it enables a driver (the 43xx driver), and when I turn it off it disables it? Thank you :)

---

### Post by dstew on 2008-02-23
You can install BUM (boot-up manager) using synaptic, and see if you can do what you want there. It is a little more sophisticated than the Services menu in System --> Administration. It allows you to tell the scripting system when to run your scripts.
EDIT: Actually, on second glance, if you just go to System --> Administration --> Services, select the service you are talking about, and click "Properties". Then you can define the run level parameters, if you want it to be killed before other processes.

---

