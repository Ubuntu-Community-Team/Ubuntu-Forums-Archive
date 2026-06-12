---
title: "What are your experiences running KMail on Xubuntu?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-12-01
Are there notorious issues with running KMail on a Xubuntu system?
The reason I'm asking is that I've just installed KMail on Xubuntu 7.04, and when I'm commanding kmail from the terminal it starts but sounds off a large number of error messages:
```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 5681
WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "move_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "copy_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "jump_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "remove_duplicate_messages"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "cancel"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "inc_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "dec_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "select_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "inc_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "dec_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "select_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "delete"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "edit"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "use_template"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x815d9d0 ): KAccel object already contains an action name "display_message"
```
I'm not asking you how to fix this problem, but curious what your experience of running KMail on a Xubuntu system is, thanks.

---

### Post by SunnyRabbiera on 2007-12-01
well does it mess up when you run it outside the terminal?
I know I get strange error messages sometimes when using KDE apps like konqueror in the terminal (mainly for recovery though as konqueror is better at setting certain folder permissions then nautilus)

---

### Post by Blofeld on 2007-12-01
Good point, actually. ;)
It doesn't show up in the menu (and I've tried editing the kmail.desktop file) and Xfce4 Appfinder lists it, but can't start it.
OK, I'm going for Thunderbird then.
Thanks for the pointer.

---

