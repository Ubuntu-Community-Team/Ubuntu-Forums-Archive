---
title: "All ubuntu programs close and ubuntu freezes"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by adamtaste on 2007-06-05
Basically it starts after i update everything on fiesty fawn and i open up firefox and it closes without an error or warning, then it happens to my applications, even to my add/remove and sometimes even to my terminal

And then it'll randomly freeze as well making me reboot

I know it isnt a hardware problem, it is deffinatly to do with ubuntu, any ideas?

---

### Post by aeiah on 2007-06-05
see what your error logs have to say about things. if you cant get to them via the gui (they're in your menu under system), they're located at /var/log/messages

---

### Post by adamtaste on 2007-06-05
[QUOTE=messages] Jun  5 15:29:06 adam-laptop gconfd (root-6016): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  5 15:29:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  5 15:29:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  5 15:29:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  5 15:30:06 adam-laptop gconfd (root-6016): SIGHUP received, reloading all databases
Jun  5 15:30:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  5 15:30:06 adam-laptop gconfd (root-6016): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  5 15:30:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  5 15:30:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  5 15:30:06 adam-laptop gconfd (root-6016): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  5 15:30:06 adam-laptop gconfd (root-6016): GConf server is not in use, shutting down.
Jun  5 15:30:06 adam-laptop gconfd (root-6016): Exiting
Jun  5 15:36:04 adam-laptop gconfd (root-6290): starting (version 2.18.0.1), pid 6290 user 'root'
Jun  5 15:36:04 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  5 15:36:04 adam-laptop gconfd (root-6290): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  5 15:36:04 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  5 15:36:04 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  5 15:36:04 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  5 15:36:34 adam-laptop gconfd (root-6290): SIGHUP received, reloading all databases
Jun  5 15:36:34 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  5 15:36:34 adam-laptop gconfd (root-6290): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  5 15:36:34 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  5 15:36:34 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  5 15:36:34 adam-laptop gconfd (root-6290): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  5 15:36:34 adam-laptop gconfd (root-6290): GConf server is not in use, shutting down.
Jun  5 15:36:34 adam-laptop gconfd (root-6290): Exiting[/QUOTE]

theres alot more of messages but basically thats it, i dont know if its a problem or not

---

### Post by adamtaste on 2007-06-05
ps i did find this 

[HTML]un  5 15:06:38 adam-laptop kernel: [   90.291864] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Jun  5 15:06:38 adam-laptop kernel: [   90.294477] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jun  5 15:06:38 adam-laptop kernel: [   90.321898] psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
Jun  5 15:06:39 adam-laptop kernel: [   91.297574] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jun  5 15:06:39 adam-laptop kernel: [   91.307304] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jun  5 15:06:39 adam-laptop kernel: [   91.311958] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jun  5 15:06:39 adam-laptop kernel: [   91.314568] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jun  5 15:06:39 adam-laptop kernel: [   91.317543] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Jun  5 15:06:39 adam-laptop kernel: [   91.317547] psmouse.c: issuing reconnect request[/HTML]

---

### Post by apos on 2008-02-23
Add "i8042.nomux=1" to your kernel boot parameter list and the problem should be gone!

(GERMAN) [http://forum.ubuntuusers.de/topic/84596/?p=1245699#1245699](http://forum.ubuntuusers.de/topic/84596/?p=1245699#1245699)

---

