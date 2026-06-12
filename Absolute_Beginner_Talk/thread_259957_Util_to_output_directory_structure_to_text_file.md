---
title: "Util to output directory structure to text file"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by andb on 2006-09-18
Is there a utility, preferably command line, to output directory structure to a text file? Like `tree` from dos? Thanks!

---

### Post by Najand on 2006-09-18
tree is available in ubuntu:
Install it at:
```

*sudo aptitude install tree*

```

([COLOR="Red"]Note:[/COLOR] It is a *universe* application... If you haven't enabled it yet, do the following:
Click: System -> Administration -> Software Properties
Then CHECK all unchecked options.)

If you want to save the output to a file.. for example DIRSTRUCT, do
tree > DIRSTRACT

---

