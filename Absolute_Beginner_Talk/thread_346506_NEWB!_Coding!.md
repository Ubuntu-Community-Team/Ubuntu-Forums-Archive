---
title: "NEWB! Coding!"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Shafferalex on 2007-01-25
I'm a newb to linux and i want to know about some basic command codes. What are some basic command codes?

---

### Post by Tomosaur on 2007-01-25
cd = Change Directory.
ls = List directory contents
cp = Copy file to somewhere else
mv = Move file to somewhere else, and/or rename file.
rm = Remove file
rmdir = Remove an empty directory
man <command> = Help page for a particular command, for example 'man rm' will bring up the help page for the rm command.
cat = Print contents of file to standard output, eg: 'cat myFile.txt'
grep <string> <file or string> = Find occurences of string in a file or a string, for example: 'grep "hello" ./myFile.txt'

If you want a further challenge, open up a terminal, hit the tab button twice, and press y when prompted. Have fun :)

You should also know about redirects and pipes:
<command1> > filename = Redirect the output of command1 to filename, for example:
```

ls -R / > myEntireSystem.txt

``` (that one may take a while :P)

<command1> | <command2> = Take the output of command 1, and use it as the input of command 2, for example:

```

ls -R / | grep '.txt'

```
will find all files with .txt in the title. There are far better ways to do this, but it's just an example.

---

