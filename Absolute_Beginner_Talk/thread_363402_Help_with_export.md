---
title: "Help with export"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by rwhillman on 2007-02-16
I am having problem opening large files in openoffice and someone suggested this solution, which I need help on in understanding how to implement --

Found the answer. For those that need it, simply add

export MALLOC_CHECK_=2

to /usr/bin/openoffice.org-2.0

i.e. the script that calls /usr/bin/soffice.

That's it - simple!

---

### Post by jvc26 on 2007-02-19
By the sound of it its suggesting adding ```
export MALLOC_CHECK_=2
``` to the file /usr/bin/openoffice.org-2.0 which is the script which calls the Open Office. I have no idea whether this would work or whether it could badly break your OO - do you have a link to the original instructions? I'm pretty sure thats what it means.
Il

---

