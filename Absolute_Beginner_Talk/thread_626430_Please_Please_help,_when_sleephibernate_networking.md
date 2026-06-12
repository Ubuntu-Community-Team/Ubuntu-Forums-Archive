---
title: "Please Please help, when sleep/hibernate networking doesn't work."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-11-29
please please help. I just want a stable experience here. 

Sometimes when resuming from sleep/hibernate wireless doesn't work. Usually wired works fine. But sometimes wired doesn't even work.

In some acpi file i tried adding STOP_SERVICES = "networking nm-applet" 
and that didn't work..

any other ideas?

Oh yah, when i try to go to manual settings on the networking applet, it shows a BLANK network manager window! Blank!

---

### Post by Threbus5 on 2007-11-29
Check the sleep/hibernate settings for disabled activities, enable them all then disable them singly to see which one causes the network loss.
That may at least provide a direction to the solution.

---

### Post by systemintheglitch on 2007-11-29
> **Threbus5 said:**
> Check the sleep/hibernate settings for disabled activities, enable them all then disable them singly to see which one causes the network loss.
That may at least provide a direction to the solution.

Sorry.. Could you elaborate just a little bit.. I don't know much about linux/ubuntu.
Where can I find these disabled activities?

---

### Post by systemintheglitch on 2007-12-12
Could someone please answer my last question.. How to do this methodical testing of which service is causing the crash?

---

