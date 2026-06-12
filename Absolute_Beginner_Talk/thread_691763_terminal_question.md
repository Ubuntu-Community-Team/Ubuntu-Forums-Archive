---
title: "terminal question"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by tone33 on 2008-02-08
My stupid question of the day is.....



when I'm trying to get to a directory with a space in the name how do I do that?

for example the directory "Program Files" exists in the .wine directory.  

cd Program Files

doesn't work.

---

### Post by taurus on 2008-02-08
```
cd "Program Files"
```
or

```
cd Program\ Files
```

---

### Post by ispy on 2008-02-08
.

---

### Post by tone33 on 2008-02-08
> **taurus said:**
> ```
cd "Program Files"
```
or

```
cd Program\ Files
```

worked perfectly - thanks!

---

### Post by spiderbatdad on 2008-02-08
looks like you would need a complete path, as Program Files is not in your home directory. I don't know where .wine is, but lets say it is hidden in your home directory. When you open the terminal from your desktop you are in your home directory so ```
cd /.wine/Program Files
``` all paths are case sensitive. so Program files would be different from Program Files. If .wine were located in /usr/share... you would need: ```
cd /usr/share/.wine/Program Files
```

---

### Post by kbless7 on 2008-02-08
> **spiderbatdad said:**
> looks like you would need a complete path, as Program Files is not in your home directory. I don't know where .wine is, but lets say it is hidden in your home directory. When you open the terminal from your desktop you are in your home directory so ```
cd /.wine/Program Files
``` all paths are case sensitive. so Program files would be different from Program Files. If .wine were located in /usr/share... you would need: ```
cd /usr/share/.wine/Program Files
```

No you would need to do 

```
cd "/.wine/Program Files"
```

or

```
cd /.wine/Program\ Files
```

---

### Post by spiderbatdad on 2008-02-08
> **kbless7 said:**
> No you would need to do 

```
cd "/.wine/Program Files"
```

or

```
cd /.wine/Program\ Files
```

3X?:lolflag:

---

### Post by tone33 on 2008-02-09
Actually I thought I'd try something like this:

```
cd "Program Files"
```

or maybe

```
cd Program\ Files
```

:lol:

---

