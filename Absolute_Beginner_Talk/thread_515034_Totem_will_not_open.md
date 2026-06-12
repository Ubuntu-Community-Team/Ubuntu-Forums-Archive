---
title: "Totem will not open"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by mudflap5 on 2007-08-01
I'm trying to get Totem (xine) up and running, with little luck.

Using Kubuntu, the program is installed, but when I click on the shortcut, a new screen opens, the title bar says "Totem Movie Player", 
the little hour glass symbol spins and spins, and a blank screen, but nothing else happens. I have tried to uninstall and reinstall the program several times, and it still does not work.  Can anyone help?
Thanks.

---

### Post by milosz.galazka on 2007-08-01
Hello,

I got similar problems with couple of applications (for example kvpnc).  My problem was that those application were running in the background without sign of life so check

ps ax | grep totem

as this can help.

---

### Post by reckless2k2 on 2007-08-01
you would have to kill them then or bring them to the foreground using fg at the cli.

---

### Post by milosz.galazka on 2007-08-01
kill -9 :)

---

### Post by mudflap5 on 2007-08-02
I typed     ps ax | grep totem     in Terminal, and Totem still w/n open.
Am I supposed to look for something in particular after using this command?
 



> **milosz.galazka said:**
> Hello,

I got similar problems with couple of applications (for example kvpnc).  My problem was that those application were running in the background without sign of life so check

ps ax | grep totem

as this can help.

---

### Post by mudflap5 on 2007-08-02
I have no idea what this means. Can you provide any more details?

Thanks



> **reckless2k2 said:**
> you would have to kill them then or bring them to the foreground using fg at the cli.

---

### Post by mudflap5 on 2007-08-02
Typed    kill -9     in Terminal and Totem will not open.  Am I supposed to do something else after this?


Thanks.



> **milosz.galazka said:**
> kill -9 :)

---

### Post by milosz.galazka on 2007-08-02
Hi,

If you see that Totem is running after ps command then you can kill it by using *kill -9 pid* where pid is a number in first column.

---

### Post by mudflap5 on 2007-08-02
Entered the ps command and found that Totem was not running.  Is there anything else I can try to get Totem to run?

---

### Post by RomeReactor on 2007-08-02
Hi. Try running Totem from Konsole:
```
totem
```
If it outputs any error messages, post them here.

---

### Post by mudflap5 on 2007-08-02
Here is the results on Totem in Konsole:







                desktop:~$ totem
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: not found

---

### Post by haldor61 on 2007-10-21
i have same problem with
"Gtk-ERROR **: Invalid type: GtkRadioButton
aborting...
Aborted (core dumped)"
error

---

