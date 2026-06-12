---
title: "listing directories using wildcard without showing the contents inside the directory?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by xl_cheese on 2007-07-09
Example.

I want to list all the contents in a directory using a wildcard, but I don't want to see the contents of the subdirectory.  I just want to see a list of the directory names.

How do I do that?

---

### Post by kfrance on 2007-07-09
I'm probably not understanding your question.  ls * [directory_name] should do it right?  It won't list the subdirectories unless you have an alias for ls that has some other options.

---

### Post by MikeDX on 2007-07-09
what you probably want to do is:

```
ls -la | grep wildcard
```

so, 

```
ls -la | grep myfile
```

will list all files and folders with "myfile" within the name...

---

### Post by xl_cheese on 2007-07-09
ex/  from my /usr directory I execute

 ls -ltr l*

It will show me everything inside the directories starting with l. I don't want to see what's in them I just want to see the directory names with time stamps next to them.

---

### Post by xl_cheese on 2007-07-09
> **MikeDX said:**
> what you probably want to do is:

```
ls -la | grep wildcard
```

so, 

```
ls -la | grep myfile
```

will list all files and folders with "myfile" within the name...

ls -la | grep myfile works, but the wildcarding does not do anything.

One step closer.  thanks.

---

### Post by bodhi.zazen on 2007-07-09
ls -lad <directory>

where <directory> is the directory to list. You can "filter" the results with grep if you like.

---

### Post by xl_cheese on 2007-07-09
> **bodhi.zazen said:**
> ls -lad <directory>

where <directory> is the directory to list. You can "filter" the results with grep if you like.

:guitar:

---

