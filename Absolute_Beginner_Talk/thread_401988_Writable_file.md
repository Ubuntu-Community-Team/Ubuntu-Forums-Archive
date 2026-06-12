---
title: "Writable file"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by logicus on 2007-04-05
Hi there

I'm trying to edit a config file.

However, when I try to edit that particular file , I get a message saying it's not writable. 

So how do I make it writeable ?

And how do i write to it ? Cause I'm guessing this involves using the (horror music) Terminal ?
#-o

---

### Post by Jussi Kukkonen on 2007-04-05
> I get a message saying it's not writable. 
Exact error messages are usually preferable -- I'm guessing in this case you are told you do not have the permissions to write?

If this is the case (you are probably trying to edit a system wide config file) try this:
```
gksudo gedit /path/to/file
```

(gksudo give you root permissions for this command and gedit is the Gnome editor)

---

### Post by logicus on 2007-04-05
Thanks,man.
That really solved it 

 :grin:

---

