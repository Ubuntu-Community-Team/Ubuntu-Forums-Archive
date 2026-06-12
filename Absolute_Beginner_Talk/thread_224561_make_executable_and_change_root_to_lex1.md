---
title: "make executable and change root to lex1"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-28
TO make a file exe please.
chown revisted from post before thanks for reply

lex1

---

### Post by Indras on 2006-07-28
You change the ownership of a file with the command "chown", like this:

```
chown <user>:<group> <filename>
```

Since the files you're trying to change belong to root, you need to run it as sudo.  So:

```
sudo chown lex1:lex1 <filename>
```

To change whether or not something is executable, you need to change the permissions on the file, with "chmod".

```
chmod <permissions> <filename>
```

To make a file executable, you just use:

```
chmod +x <filename>
```

There's lots more depth into the chmod command, for instance, you can assign file permissions by their octal value.  Google for deeper info.

---

