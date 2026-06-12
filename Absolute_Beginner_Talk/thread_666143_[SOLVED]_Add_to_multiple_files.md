---
title: "[SOLVED] Add to multiple files?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by mouseboyx on 2008-01-13
is it possible to do something similar to:

echo "add this to a bunch of files" >> *.html

but this creates a file *.html 

How would i add a line to many files at once?

---

### Post by PeterJS on 2008-01-13
Try
```

echo "Hello World" | tee -a *.html > /dev/null

```

---

### Post by napzilla on 2008-01-13
Assuming that all the files you want to append the name to are in the same directory, you could use this:

```
for file in $(ls *.html);
do
    echo "Append this to my file." >> ${file};
done;
```

```
for file in...
``` tells the bash to cycle through a series of values for the variable *file*.

```
$(ls *.html)
``` simply instructs the shell to run the *ls* command, and return each instance of output as a value for *file*.

```
${file}
``` is how you tell the shell to use the current value for *file*.

The semicolons just indicate the end of the command. You can enter a *for* loop at the command line either one line at a time, or by using the semicolons.

If your files are in multiple directories, then you *might* be able to do this using *find* or *locate* instead of *ls*...

Presumably you already know what the rest of the command means...

---

### Post by mouseboyx on 2008-01-13
Thanks!

---

