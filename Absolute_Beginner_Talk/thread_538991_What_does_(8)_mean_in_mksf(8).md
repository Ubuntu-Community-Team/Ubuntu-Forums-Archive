---
title: "What does (8) mean in mksf(8)?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-08-30
I read this in a man page.It's said
SEE ALSO
mksf( 8 ) .
Thanks in advance.

---

### Post by jspangler on 2007-08-30
The (8 ) refers to another manual file. You can open this manual by typing into terminal:

```
man mkfs
```

This is true of many programs that also have manuals. For example, "man apt-get" opens the manual for apt-get. This is a very helpful feature!

EDIT: I see you were already in a man file, so I didn't have to tell you how to open another one! :-)

---

### Post by sumguy231 on 2007-08-30
8 is the manual section which that program's manpage is in - in this case, it's 8 for system administration commands.

---

### Post by Hxsrmeng on 2007-08-30
> **jspangler said:**
> The (8 ) refers to another manual file. You can open this manual by typing into terminal:

```
man mkfs
```

This is true of many programs that also have manuals. For example, "man apt-get" opens the manual for apt-get. This is a very helpful feature!

EDIT: I see you were already in a man file, so I didn't have to tell you how to open another one! :-)

thanks. But why some times, 
SEE ALSO don't add ( 8 ) to some programs?

---

### Post by steve.horsley on 2007-08-30
By default man will only show you one page. For instance, **man man** shows you one page. It doesn't even bother to tell you there are other pages.** man -a** shows all pages on the subject. **man -a man** will show you two pages on man, from chapters 1 and 7.

---

### Post by Hxsrmeng on 2007-08-31
> **steve.horsley said:**
> By default man will only show you one page. For instance, **man man** shows you one page. It doesn't even bother to tell you there are other pages.** man -a** shows all pages on the subject. **man -a man** will show you two pages on man, from chapters 1 and 7.

Thanks.

---

