---
title: "Problems running opera."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Daredemo on 2007-08-02
I have been having some problems when running opera on my computer. The browser runs ok most of the time. But when I visit a page that uses flash, it suddenly begomes extremely sluggish. Additionally, I've discovered when trying to watch a video on youtube, that not only it becomes very slow, but it also has no sound.

When running opera from the terminal it returned the following message:

> 
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(process:6518 ): GLib-GObject-CRITICAL * * : gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:6518 ): Gtk-CRITICAL * * : gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);


I would like to add that I had the same problem with firefox initially, but after running some updates it was fixed.

---

### Post by milosz.galazka on 2007-08-02
Hello,

Maybe problem is connected to [this]("http://my.opera.com/community/forums/topic.dml?id=183923")?

---

### Post by Daredemo on 2007-08-02
It seems not. They said the problem was fixed after getting the newest version of opera, I have version 9.22 and I still get this problem. I will try to purge and reinstall it, can't hurt.

---

### Post by milosz.galazka on 2007-08-02
I installed opera and flash is working fine and sound on youtube works too.
Maybe try to change name of *~/.opera* directory and then run it?

---

### Post by ev5unleash1 on 2007-08-02
It could of been how you get the Flash for it. There could be one pasificly or modified to work with oprea linux.

---

