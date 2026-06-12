---
title: "aMSN file sending not possible :("
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-10-27
For some reason, when I try to send files using aMSN (latest release, not the one on the repos), my contacts can't even see that I'm trying to send them anything. Also, it says that I can't use webcam because of my firewall settings, and this is a fresh install of Edgy, I've done nothing to the firewall! Anyone else solved this problem?

---

### Post by franestepona on 2006-10-27
same problem here, but in my case tk causes the error (I didnt have any problem before installing tk and tcl or whatever is called) Anyone to help?
Thanks!

---

### Post by happy-and-lost on 2006-12-17
AH HAH!

On aMSN's main window, press Ctrl-S and paste the following...

```
 set ::abook::demographics(listening) true
```

EDIT: Anyone any ideas on making this fix permanent?

---

