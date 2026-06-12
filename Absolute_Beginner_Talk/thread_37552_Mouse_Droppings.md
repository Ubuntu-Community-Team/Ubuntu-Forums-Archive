---
title: "Mouse Droppings"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by F1_error on 2005-05-27
I've got a USB optical mouse plugged into my Ubuntu box. For some reason, that I can't figure out, it stops working from time to time. I can get it back by unplugging and pluggiing it back in. But this is kind of a pain, since the USB port is in the back of the machine. 
Is there something I can do to keep it from being dropped?

---

### Post by Mez on 2005-05-28
I dont think there's anything you can do to stop it being dropped.... but restarting the hotplug subsystem should start it again

just try this from a console

sudo /etc/init.d/hotplug restart

Tats the thihg about linux.... my mouse is very... unreliable in windows if I reboot... it will sometimes not powe up properly, and i have to do a hard rreboot to get it working., however, the hotplug subsystem makes it work perfectly in linux every time... :D

---

