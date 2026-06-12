---
title: "fails to start x server after attempt fix resolution"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by clinty on 2007-06-05
I tried to fix the screen resolution and now i'm stuck

---

### Post by meatpan on 2007-06-05
Can you share some more details about your problem?

When the x server fails, an error message is typically written to a file in the /var/log directory.
Try running: 'sudo less /var/log/Xorg.0.log', and look for lines starting with the characters 'EE'

---

