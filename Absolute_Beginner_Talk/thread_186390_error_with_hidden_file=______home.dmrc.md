---
title: "error with hidden file=      home/.dmrc"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by mike_m on 2006-06-01
when i boot i get an error box that $HOME/.dmrc has the wrong perms & should be 644 & it will not load.

OK. ubuntu seems to run fine but the error box bugs me, so I found the hidden file .dmrc & change it to 644 & rebooted, but the error is still there, & now the file is already 644 so the error is wrong

what am I doing wrong?

Thanks!

---

### Post by sinkxdie on 2006-06-01
sudo chown "username" 644 "file"

i think?

---

