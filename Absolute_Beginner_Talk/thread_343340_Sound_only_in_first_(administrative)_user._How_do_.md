---
title: "Sound only in first (administrative) user. How do I fix this? [Resolved]"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by gyalakias on 2007-01-21
Hmm, this seems to be an unusual problem.

The sound works fine when I log-in as a first (administrative) user, but it doesn't work when I log-in as a normal (non-administrative) user. I go to the sound settings.

They are there when I log-in as admin, but not completely blank when I log-in as guest.

Can anybody tell me what's wrong and how I can fix it?

Thanks

---

### Post by aysiu on 2007-01-21
This command should help: ```
sudo adduser *username* audio
``` where *username* is the name of your non-administrative user.

---

### Post by gyalakias on 2007-01-21
Thank you!

---

