---
title: "How do I . . ."
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-02-24
How do I copy 2 txt files into one?

i.e. file1.txt + file2.txt > file3.txt

---

### Post by Stormy Eyes on 2006-02-24
Try the following:

```
cat file1.txt file2.txt >> file3.txt
```

The "cat" command will take the contents of file1 and file2 and blast them to standard output (which is usually your screen). Using ">>" will redirect the output of cat into "file3.txt". Hope this helps.

---

### Post by Tichondrius on 2006-02-24
^^ not exactly, because >> will append to the end of the file, > will write it to the file from scratch

Method 1:
```

cat file1.txt file2.txt > file3.txt

```

Method 2:
```

cp file1.txt file3.txt
cat file2.txt >> file3.txt

```

---

### Post by Stormy Eyes on 2006-02-24
[QUOTE=Tichondrius]^^ not exactly, because >> will append to the end of the file, > will write it to the file from scratch[/QUOTE]

That's true. However, if the file doesn't exist to begin with, then >> is fine.

---

### Post by My-dial-up on 2006-02-24
Many thanks people.

Next question, if I wanted to do this once a day, how would I set up the crontab job?

---

