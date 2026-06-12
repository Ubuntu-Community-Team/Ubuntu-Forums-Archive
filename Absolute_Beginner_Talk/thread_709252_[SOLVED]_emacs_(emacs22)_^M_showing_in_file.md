---
title: "[SOLVED] emacs (emacs22) ^M showing in file"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-02-27
Hi,

I've created a file in a DOS editor, and now I've opened it in emacs22, and the end of line always shows a ^M sequence.  I assume this is because DOS files have a carriage turn and a line feed and linux files only have the carriage return (or only the line-feed, cant remember which).

Is there an option to select that will not display this ^M char?

This happens also in gvim.

thanks

---

### Post by taurus on 2008-02-27
Try running

```
dos2unix *filename*
```
That would strip the ^M at the end of each line that DOS puts in.

---

### Post by Beggar on 2008-02-27
Im assuming you know how to edit your .emacs file.

```

;; keep out those ^M characters
(set-buffer-file-coding-system 'unix)

```

---

### Post by mali2297 on 2008-02-27
Just curious, why have you used a DOS editor? :-s

---

### Post by aBitLater on 2008-02-28
> **mali2297 said:**
> Just curious, why have you used a DOS editor? :-s

What? You don't use DOS?  I thought everyone did?  :) :) :)

I set up dosemu so I could write some 16-bit applications in masm assembly. hehe, about a day after I installed dosemu, it dawned on me that accessing my c:\ drive in the dos box was easy to do from a linux prompt, at ~/.dosemu/drive_c/

---

