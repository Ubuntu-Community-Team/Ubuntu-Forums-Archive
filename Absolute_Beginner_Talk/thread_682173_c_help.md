---
title: "c help"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by rob21 on 2008-01-29
I have three files-driver.c, strmatch.c and file.in with the sentences that I want to pipe into my driver program. At the terminal using c and linux, after I compile all  the files I enter  "driver < file.in > file.out" to get the program to parse the info in file.in but cannot get program to work. Please tell me what I am doing wrong.
                         thanks

---

### Post by LaRoza on 2008-01-29
> **rob21 said:**
> I have three files-driver.c, strmatch.c and file.in with the sentences that I want to pipe into my driver program. At the terminal using c and linux, after I compile all  the files I enter  "driver < file.in > file.out" to get the program to parse the info in file.in but cannot get program to work. Please tell me what I am doing wrong.
                         thanks
You need to specify the path if it in not in your $PATH.

```

./driver <file.in> file.out

```

The "." means cwd.

---

