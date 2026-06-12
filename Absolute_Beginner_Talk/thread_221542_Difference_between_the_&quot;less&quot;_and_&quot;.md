---
title: "Difference between the &quot;less&quot; and &quot;more&quot; commands?"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by BlueStreak on 2006-07-23
It appears to me that "less" and "more" do the same thing.  Please explain the difference and when I should use one over the other.  Thanks

---

### Post by bigzak on 2006-07-23
The basic difference is that 'more' simply displays a file a single line or page at a time, 'less' is a full blown 'pager' application. This means that you can scroll up and down within the file, search using regular expressions, shell out to an editor, and many other things. So, they basically do the same job (display text files), but the manner in which they do this is completely different. Best way to find out is to try it :)

---

### Post by christhemonkey on 2006-07-23
From the more man page:
[QUOTE="more man page"]
More is a filter for paging through text one screenful at a time.	
This version is especially primitve.  Users should realize that less(1) pro-vides more(1) emulation and extensive enhancements.
[/QUOTE]

[QUOTE="less man page"]
Less is a program similar to more (1), but which allows backward	 move-ment in the file as well as forward movement.
Also, less does not have to read the entire input file before  starting, so with large input files it  starts up faster than text editors like vi.
[/QUOTE]

So in summary, with less you can scroll back up! :D

---

### Post by jstueve on 2006-07-23
man less
man more

less is GNU and has some enhancements
more is under BSD

---

### Post by ciscosurfer on 2006-07-23
Among other things, "less" allows you to scroll back up within a terminal (try the up arrow)...."more" does not allow this functionality.  From the more manpage:> More is a filter for paging through text one screenful at a time. This version is especially primitve.  Users should realize that less(1) provides more(1) emulation and extensive enhancements.Read the manpages for both "less" and "more" like this```
man less
man more
```

---

