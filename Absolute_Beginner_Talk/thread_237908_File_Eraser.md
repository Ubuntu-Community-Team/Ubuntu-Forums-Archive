---
title: "File Eraser"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by CanonD on 2006-08-16
Is there a secure file eraser in linux?

Something easy like eraser in windows ([http://www.tolvanen.com/eraser/](http://www.tolvanen.com/eraser/))

---

### Post by Third Thoughts on 2006-08-16
If you're not afraid of the command line then you can get wipe. Just 
```

apt-get install wipe

```

~Andrew S.

---

### Post by LadyDoor on 2006-08-18
And if you're *really* paranoid, you could you **shred** and *then* **wipe.**

---

### Post by statue on 2006-08-18
shred is the default command to overwrite files, use the -u option to delete the file(s) after they have been overwritten.

ex: shred -uvz <path/filename>

---

### Post by Marsolin on 2006-08-18
You can also try Gringotts ([http://linuxappfinder.com/package/gringotts](http://linuxappfinder.com/package/gringotts)).  It has a Gtk interface.

---

