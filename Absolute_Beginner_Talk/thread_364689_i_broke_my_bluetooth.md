---
title: "i broke my bluetooth"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-02-18
i uninstalled and then installed my bluez-utils package and now, my mouse and keyboard wont auto reconnect anymore. even in discoverable mode....

any ideas what could be wrong?

Thanks

---

### Post by Old Pink on 2007-02-18
What do you have to do to make them connect? :)

---

### Post by jinxjinx on 2007-02-18
i can scan for the devices with 
sudo hcitool scan
and connect with
sudo hidd --seach
or 
sudo hidd --connect 00:03:C9:C3:72:7C

and when i type dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable


i get a little pop up that tells me its in discoverable mode, but its not auto connecting anymore...

thanks for the help

---

### Post by Old Pink on 2007-02-18
If you head to System > Preferences > Sessions, and put:
sudo hidd --connect 00:03:C9:C3:72:7C
In the startup list, that should connect it at startup.

Try re-pairing everything manually. Delete all traces of the keyboard/mouse and the computer knowing each other, then re-introduce them. :)

---

### Post by jinxjinx on 2007-02-18
specifically what should i delete?
and how do i pair manually?

thanks

---

