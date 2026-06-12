---
title: "How do I copy content from file to file?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-06-03
How do I copy the content from file to file and overwrite anything?

Assume the content inside file1 says:

The content inside here will be overwritten!

Assume the content inside file2 says:

The content inside here will be copied.

What can I do to copy the content inside file2 over to file1?  And whatever was in file1 before would be overwritten?

Yes, I am aware of the mv command can do the same.  I am just trying something out for a script.

---

### Post by xenmax on 2006-06-03
```
cat foo > foo1
```
where file foo has content to be copied over to file foo1. Note that  foo1 will be  *entirely* over-written and you will lose previous contents of foo1.

---

### Post by steve.horsley on 2006-06-03
The easiest way is:
> cp file2 file1

---

