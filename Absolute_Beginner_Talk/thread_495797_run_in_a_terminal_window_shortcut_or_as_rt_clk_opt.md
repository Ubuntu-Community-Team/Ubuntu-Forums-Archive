---
title: "run in a terminal window shortcut or as rt clk option"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-07-08
Is there either a shortcut ctrl-alt-? or a way to add "open in terminal" to right click options in Feisty?  I would have sworn I had the option installed or whatever in Edgy.

---

### Post by trinaryouroboros on 2007-07-09
Most shell scripts you double-click in Ubuntu give you an option (checkbox) before loading them that says "Run in Terminal" - however, if you need the option available from the Right-click menu, I would presume you would hunt for some kind of Nautilus Script.

I found a handful of nice Open Terminal Here scripts on this page:

[http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)

If you found a good choice of script, make sure it's executable:

```
chmod +x *scriptname.sh*
```

Then copy it to **/home/*yourname*/.gnome2/nautilus-scripts**

When you want to run it, just right-click the file and choose Scripts -> Whatever-script

:guitar:

---

