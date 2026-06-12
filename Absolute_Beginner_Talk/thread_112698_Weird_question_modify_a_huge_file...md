---
title: "Weird question: modify a huge file.."
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by veraction on 2006-01-04
So, I have a 3GB+ ASCII file (containing numeric data) & I want to remove the last line from it. How would I go about doing this? I can't load it in a text editor since I only have 1GB RAM + 600MB swap. 

The way I've done it is:
```

$ wc -l file.txt
$ head -n (N-1) file.txt > tmp.txt #where N is the number of lines in the file
$ rm file.txt
$ mv tmp.txt file.txt

```

Or how would I modify the start/middle of the file?

I think using a MySQL database or something to store these values would create a  fair amount of overhead, but I'm not sure.

Comments/Ideas?

[edit] I've had to modify middle of file in past & have done so using a python script, but hard/takes time to do it every time.

btw, I only need to modify this file occasionally to fix computed values

---

### Post by xmastree on 2006-01-04
I'm pretty sure you can do it with **sed**

But I've never tried...

---

