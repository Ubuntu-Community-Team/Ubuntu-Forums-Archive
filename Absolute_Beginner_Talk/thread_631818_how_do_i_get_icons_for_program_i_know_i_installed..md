---
title: "how do i get icons for program i know i installed."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by TheTeZ on 2007-12-04
hey, i have kubuntu, and im curious ... how do i start a program that i installed... for example kmail.   and how do i create an icon to throw in my quick launch bar or even my kmenu

---

### Post by Sarteck on 2007-12-04
Right-click on your K-Menu, and you and add/remove/edit items in your K Panel.  But, for programs that you want to add to your K Menu or K Panel, you have to know the command to start them, and just enter it into the K Menu Editor.  :)

---

### Post by TheTeZ on 2007-12-04
thanks for the quick reply.... now ... what would the command be to run Kmail... it was installed with the o.s.

---

### Post by sethvath on 2007-12-04
kmail

to start it minimized: kmail ; dcop kmail kmail-mainwindow#1 close

---

### Post by SOULRiDER on 2007-12-04
Not that its "kmail" not "Kmail", it's all lowercase.

---

### Post by TheTeZ on 2007-12-04
right.... 

Yeah, thanks ... all worked out, 

if i wanted to do other programs, would that same script diffrent program name work?

---

### Post by SOULRiDER on 2007-12-04
Just create a shortcut to it using the kMenu editor and use the name of the program to run it, its as easy as that :)

---

### Post by TheTeZ on 2007-12-05
when i start kmail with  this code
kmail ; dcop kmail kmail-mainwindow#1 close
 kmail starts up with terminal and displays the junk below.... it starts and gets to load the messages, then crashes.... any ideas on how to fix it.... i basically wanna have kmail open when i open it and minimize it so its hidden, and i want alerts when i get mail....  if i leave it...   i can open the program by typing kmail into terminal .... but thats about it, i would like to click my icon and launch it then minimize it to the system tray....   any help?

```

  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "move_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "copy_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "jump_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "remove_duplicate_messages"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "cancel"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "inc_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "dec_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "select_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "inc_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "dec_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "select_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "delete"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "edit"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "use_template"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81894c0 ): KAccel object already contains an action name "display_message"
```

---

### Post by sethvath on 2007-12-06
Do not type the above code into terminal. It was meant for your menu entry.

---

### Post by TheTeZ on 2007-12-06
i dont type it into terminal, but it opens terminal and shows that.

---

