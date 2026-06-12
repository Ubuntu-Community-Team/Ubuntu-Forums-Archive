---
title: "php textarea problems"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Takuhari on 2008-03-05
I have a form that uses a textarea...

when i submit, it appends to a .txt file
for each submition, all the data should be in one line...
however for each return key used, it brings it down one line...
is there a way that i can make it write in the same line?

---

### Post by gerscht on 2008-03-05
Although that's not Ubuntu relevant:
replace \n with nothing like
```

$textAreaData=str_replace("\n","",$textAreaData);

```
to be on the save side also replace \r\n which is used by windows
```

$textAreaData=str_replace("\r\n","",$textAreaData);

```

---

### Post by Takuhari on 2008-03-05
Thanx ALOT!!!

That was exactly what i was looking for^^

---

