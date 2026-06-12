---
title: "[SOLVED] How to extract gzip file with no extension?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by TRANQU111TY on 2008-01-26
I have a theme I downloaded from Beryl project but I can't extract it with Archive Manager.

If I go properties on the file it says its a gzip archive. The file itself doesn't have an extension on it, perhaps I need to put one on?

EDIT: I just added the extension on the end and it worked :)

---

### Post by yabbadabbadont on 2008-01-26
If you add ```
.tar.gz
``` to the end of it, it may work.

---

### Post by LaRoza on 2008-01-26
> **yabbadabbadont said:**
> If you add ```
.tar.gz
``` to the end of it, it may work.

If it is a tarball, yes. 

The command:

```

file <filename>

```

Will give the type of file. File extensions don't mean anything, although some programs use them.

---

