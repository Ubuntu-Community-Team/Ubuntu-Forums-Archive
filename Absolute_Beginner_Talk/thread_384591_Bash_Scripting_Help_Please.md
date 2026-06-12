---
title: "Bash Scripting Help Please"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-03-14
In a script I want to check if a file is executable or not. Have it return true if it is, and false if it is not.

eg
```

# My Script
if [ file.sh is executable ] ; then
    file.sh
else
    chmod +x file.sh
    file.sh
fi

```

How can I go about doing this?

---

### Post by guysmiley25 on 2007-03-14
Never mind figured it out

```

# My Script
if [ -x file.sh ] ; then
    file.sh
else
    chmod +x file.sh
    file.sh
fi

```

---

### Post by ViRMiN on 2007-03-14
Cool, I was just going to say to use the -x test :)

---

### Post by ViRMiN on 2007-03-14
You find more options doing, "man test"

---

### Post by guysmiley25 on 2007-03-14
Chears for that I was wondering what there was available.

---

