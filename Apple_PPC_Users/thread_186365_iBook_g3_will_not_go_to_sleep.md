---
title: "iBook g3 will not go to sleep"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by mrios on 2006-06-01
Hi everyone. I just updated to Dapper and I noticed one major negative difference: my computer no longer goes to sleep properly when I shut the lid. My computer is an iBook G3 dual USB. 

Symptoms: 

1. When the adaptor is plugged in, the screen turns off when I close the laptop, but there is no indication that anything else has been placed into sleep mode.

2. When the adaptor is out, closing the lid does not turn the screen off. 

Data:

1. I am running pbbuttonsd -- it worked fine before this install.
2. The dmesg output does not change when I put the lid down.

If people need more information, feel free to ask questions. I'd like to know what to do.

---

### Post by mrios on 2006-06-01
I fixed it. It was a stupid error. I should have gone to the power management control panel located under the menu System > Preferences > power management.

I set up my laptop to suspend when the lid closes, and it worked fine.

---

### Post by saturnine on 2006-10-09
mrios-

Does suspend work every time you close the lid?  More likely than not after I close and open the lid again on my machine I get a message from power manager saying that the laptop failed to suspend.

---

