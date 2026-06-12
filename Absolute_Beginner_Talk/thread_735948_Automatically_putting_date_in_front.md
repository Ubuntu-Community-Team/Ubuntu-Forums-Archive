---
title: "Automatically putting date in front?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by persofi on 2008-03-26
Hi,
I'm wondering if this is possible in Ubuntu or if there is some software that does this for me: I want to automatically rename every textfile (or other certain file types like .ods) so that the date very it was last changed is in front of the filename.

So bla.odt would become 260308bla.odt if today was the last time I changed it.

---

### Post by ghostdog74 on 2008-03-26
getting the last change date of a file
```

# stat -c "%z" file | awk '{print $1}'
2008-03-26

```

i leave it to you to assign to variable, so that you can rename it
```

mv oldfile ${result}bla.odt

```

---

