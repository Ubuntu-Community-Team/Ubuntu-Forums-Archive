---
title: "How not to auto mount a recovery - windows partition"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by yousr on 2007-05-18
Hello ,I usually dont ask .Im a reader.
But how would I stop an auto mount for a windows recovery partition if I may ask?
So that it dose not mount on load up.
Or would I be better off writing a small startup script to unmount on load?
And how would one of you guru's go about that script?
Thanks in advace.
Please help.

---

### Post by Happy_Man on 2007-05-18
Type this command into a terminal: 
```
gksudo gedit /etc/fstab
```

and delete the entry that corresponds to your recovery partition. It will never ever mount automatically again. :)

---

### Post by yousr on 2007-05-18
Thanks

---

