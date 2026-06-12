---
title: "How do I CREATE a file and save to restricted?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Armor on 2007-01-31
I have been going CRAZY here. Brand new to Linux (running Edgy). I'm trying to get Beryl running, and I need to make a startup script called "startxgl.sh" and then save it in /usr/local/bin 

I've searched high and low. I know how to edit existing files and save them, I know how to use "gksudo nautlius" and I know how to use "gedit newfilename.sh" to make a new file, but for the life of me I can NOT seem to figure out that once my new file is created, how on earth do I get Ubuntu to give me the permissions to save it to the restricted area that it needs to be saved in?@!$ Please help!!:confused: :confused: :confused:

---

### Post by IYY on 2007-01-31
Instead of 

```
"gedit newfilename.sh"
```

use

```
"gksudo gedit newfilename.sh"
```

---

