---
title: "Scripting how to express a command in multiple lines."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-04-21
How can I express a command on multiple lines.

eg
```

sudo aptitude install package1 package2 package3 package4 package5

```

You can image if you wanted to install 100 packages it would be very long. And then say you want to edit the command in the script a remove packagex, you would have to scan thought looking for it. I feel it would be easier looking down a column than across a row.

Also I would like to comment on what each package is for. This would also be easier if the packages where listed in columns.

eg
```

aptitude install [move next line]
# This program is for doing back flips
package1 [move next file]
# This program is for doing star jumps.
package2
exit

```

Any ideas?

---

### Post by Phineas on 2007-04-21
I'm a relative neophyte as well, but why don't you simply make multiple aptitude calls on each line?

-- Phineas

---

### Post by Swab on 2007-04-21
any time you want to go to a new line just throw in a \

so..

sudo aptitude install package1 \
package2 package3 \
package4 package5

---

### Post by guysmiley25 on 2007-04-21
Chears Swab I&#314;l try that now.

And to answer Phineas question, it&#347; because it is so much more efficient to do it in one call. I have try multiple calls. And found that it took a lot longer.

---

### Post by Phineas on 2007-04-21
Gotcha, good info :)

---

