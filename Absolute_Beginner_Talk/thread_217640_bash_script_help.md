---
title: "bash script help"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-07-17
Assume this is the command I will use
```
$ script fooqwerfooasdffoozxcv
```
In the script, how do I make it add a space before foo* in $1?  This way when the script runs 'fooqwerfooasdffoozxcv' becomes 'fooqwer fooasdf foozxcv'.

In other words, when I run the script, the script will check if $1 contains the word 'foo'.  If it does, it will automatically add a space before it.

---

### Post by aysiu on 2006-07-17
I don't really know much about how to use these commands, but I believe the commands you're looking for are *awk* and *sed*.

---

### Post by tux101 on 2006-07-18
Would someone please further help?

I only know how to use sed to subtract a few things.  Not add a space per target.

---

### Post by Ragazzo on 2006-07-18
> **tux101 said:**
> Would someone please further help?

I only know how to use sed to subtract a few things.  Not add a space per target.

```

#!/bin/bash

echo "$1" | sed -e "s/foo/ foo/g"

```

Does this suffice?

---

### Post by tux101 on 2006-07-18
It worked!  Thank you so much, Ragazzo!

---

