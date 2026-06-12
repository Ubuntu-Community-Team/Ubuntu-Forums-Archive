---
title: "shutdown...won't shutdown computer"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by hillikus on 2008-03-29
I'm sure this has been asked before but nothing that I could find worked so here it is again.
When I select "shutdown" the computer will go as far as the Ubuntu screen with progress bar up until the progress bar is empty and then it will just hang there indefinitely. Once it is here I will have to hold the power button down for 5 seconds until it shuts down that way. The computer is a Gateway E-series with a P4 3.2GHz processor and I have Windows XP installed also. So far this is what I have tried to no avail:
 tried adding "apm power_off=1" to /etc/modules
 tried adding -hP to the shutdown command in /etc/acpi/powerbtn.sh (at the bottom)

Thanks in advance for your help!

-Linux noo(not even a noob yet, just a noo)

---

### Post by Joeb454 on 2008-03-29
what happens if you run ```
sudo shutdown -P now
``` from a terminal :)

---

### Post by hillikus on 2008-03-30
Still won't shutdown. 

I forgot to add that when the computer hangs at the empty Ubuntu Progress Bar all the lights on the keyboard blink as if it were shutting down and then it just stays there.

---

### Post by tad1073 on 2008-03-30
On my computer I have splash enabled and when it gets to "Will halt now" it hangs there for a second then my screen goes black w/ a flashing cursor in the top left corner of the screen, that is when I turn off my computer using the power button. 

Is that what's happening with you?

---

### Post by Sef on 2008-03-30
Check the power management settings in your BIOS.   I had a similar problem except it wouldn't restart; it would shutdown.  I changed a setting in the power management, and all worked fine after that.

---

