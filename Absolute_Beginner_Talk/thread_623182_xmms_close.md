---
title: "xmms close???"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by jorki on 2007-11-25
it shows xmms closed, but the application is still appearing...what should I do... 
the command xmms -q doesn't close xmms application...

---

### Post by kellemes on 2007-11-25
killall xmms

---

### Post by jorki on 2007-11-25
I think it doesn't work...:(

---

### Post by sailor2001 on 2007-11-25
in terminal:  pkill xmms

---

### Post by rmockler on 2007-11-25
I had exactly the same problem as you, XMMS would not shut down.  So, I killed it with the System Monitor function, then ran XMMS again.  I clicked on the configure button on the top left corner of the XMMS display, then I went to Options, Preferences and under the Output Plugin, I changed the entry from Default to my actual Intel device, clicked OK all the way back to the XMMS display and it works fine now.  It's not lightening fast, but it shuts down properly.
May or may not work on your system, my laptop is running Feisty Fawn.

---

