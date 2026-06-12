---
title: "Secure Deleted Items Folder"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by suibhne on 2008-02-22
I have been thinking-should we not be able to attach a script to the trash folder so that when we empty it, a shred like script runs automatically.

what are the problems with this and why is it not done as a default action?

is there way to run shred so that it acts on whole folders and not just individual files?

---

### Post by rapiscan on 2008-02-22
I don't think something like this is implemented because it is extremely inefficient and would add a lot of wear and tear on your harddrive.  You would have to write to disk for everything deleted instead of just removing the link to the file.

To answer your other question.  Doing something like 'shred /path/to/directory/*' should shred all files in a directory.

---

### Post by suibhne on 2008-02-25
Ah, I see, thanks a lot - I couldn't understand why this is a default action - do you think it would be practical to have an option on the trash can so that all users could do this? People unaware of 'shred' for example?

---

### Post by suibhne on 2008-02-25
ooops, I mean, NOT A DEFAULT ACTION

---

### Post by rapiscan on 2008-02-25
Generally speaking, you want to read/write from the harddrive as little as possible.  Accessing the harddrive is usually two orders of magnitude (100 times)  slower than reading/writing to RAM.  

If this were made an option to general users, they may not know or understand what kind of strain it is really putting on their system.  They might enable this option and then complain about how slow Ubuntu is.  Most likely, if you have data that is very sensitive, you would be aware of how to properly remove the sensitive data.

Anyway, this is all just my opinion, I am not a developer/maintainer.

---

