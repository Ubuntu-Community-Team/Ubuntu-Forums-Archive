---
title: "Running Python Scripts"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-09-11
I was having a problem executing python scripts in the terminal

i type


python example.py

is that right?

---

### Post by sethmahoney on 2006-09-11
> **youthforlinux said:**
> I was having a problem executing python scripts in the terminal

i type


python example.py

is that right?


Your example is "example.py"?  If so, you can either type
```
python example.py
```
or chmod the example.py file and just type
```
example.py
```

---

### Post by steve.horsley on 2006-09-11
> **youthforlinux said:**
> I was having a problem executing python scripts in the terminal

i type


python example.py

is that right?

Yes. Unless it's in a different directory, in which case you must give the path to it like this:
python /home/youthforlinux/projects/python/example.py

What message do you get when you try it? It's always good to post the error message.

---

### Post by StickyStyle on 2006-09-11
> **sethmahoney said:**
> Your example is "example.py"?  If so, you can either type
```
python example.py
``` or chmod the example.py file and just type
```
example.py
```

Just to expand upon this post, you would need to chmod the file with and execute bit with the following command at the command line
```
$ chmod +x example.py
``` and thus execute it with (providing it is in your current working directory)
```
$ ./example.py
```

---

### Post by jordanmthomas on 2006-09-11
If you make it executable, you'll need to add this at the beginning of the python script
```

#!/usr/bin/python

```

---

