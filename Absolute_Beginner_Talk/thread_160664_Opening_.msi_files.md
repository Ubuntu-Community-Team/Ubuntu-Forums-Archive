---
title: "Opening .msi files?"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Marcelino on 2006-04-15
With Wine I can open .exe files. But how can I open .msi files (with Wine, or something else?)

---

### Post by mostwanted on 2006-04-15
By searching on Google with the keywords "wine msi" I got this:

[http://frankscorner.org/index.php?p=msi](http://frankscorner.org/index.php?p=msi)

Searching is always a good way to find information.

---

### Post by hentaidan on 2006-04-15
Try ```
msiexec /i msifile.msi
``` in the terminal,

or right click and select "Open with other application", click on "Use custom command", and enter msiexec /i

Dan

---

### Post by Marcelino on 2006-04-15
Thank's a lot :rolleyes: I searched other things to make that program to work, but not this.

---

