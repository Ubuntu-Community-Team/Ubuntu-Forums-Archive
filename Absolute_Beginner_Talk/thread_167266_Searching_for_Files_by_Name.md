---
title: "Searching for Files by Name"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by charlie. on 2006-04-28
I am trying to find a file with a name that matches a pattern. The file is a binary file, so looking at the contents will not be helpful. How do I do this?

I thought I could use ls and grep to find the file, by...

ls -R | grep PHRASE

... While this did show that the file did exist below the current path, it did not help because ls does not print the full or relative paths to the files that it lists.

I though I could use grep on its own, but it kept searching the contents of the files and not the names themselves.

Any help would be appreciated. Thank you.

---

### Post by xenmax on 2006-04-28
```
find <path> -name <name of file>
``` where <path> is directory where you want to search, Eg: . for current directory
and <name of file> is exact name of file. Some wildcards are also allowed, but you may have to enclose them in quotes Eg: "*sim" for files ending in sim

Take a look at ```
man find
``` You can also specify max depth to follow sub-directories and lots of other options.

---

### Post by charlie. on 2006-04-28
Thanks xenmax, that is exactly what I was looking for.

---

### Post by steve.horsley on 2006-04-28
> locate filename
filename can be a part on the filename only if you like. The only problem is that if there is a directory matching that filename, it lists everything in the directory.

---

