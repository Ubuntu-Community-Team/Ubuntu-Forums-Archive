---
title: "remove printer"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by DanFlo on 2008-04-12
how to remove the printer that ubuntu finds because it doesn't work and i can't use it in virtualbox.
i am running ubuntu 7.10 !
thank you

---

### Post by RealPSL on 2008-04-13
I might be over simplifying this but based on your information you can simply launch the Printer Configuration tool and delete the printer. You can do this from the menu with **System > Administration > Printing**. Highlight the printer in question and click the delete button.

---

### Post by DanFlo on 2008-04-13
i already did that the printer is still there even after i delete it !

---

### Post by DanFlo on 2008-04-13
any more suggestions regarding this?
please advice!

---

### Post by RealPSL on 2008-04-14
Well that sounded like a bug to me and should be reported as such. If you are willing to try from the command line you can run ```
lpadmin -x printer_name
```

---

