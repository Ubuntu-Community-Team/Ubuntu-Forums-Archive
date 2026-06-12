---
title: "[SOLVED] Find different file types"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by lambono on 2008-04-16
Quick one for you... 

I would like to recursively search from a base directory and delete all music files older that 10 days old. 

I can delete all mp3s using...

find $BASE_DIR -type f -iname *.mp3 -mtime +10 -exec rm {} \; 

How can I also include other extensions?

Thanks.

---

### Post by Claus7 on 2008-04-16
Hello,

```
find $BASE_DIR -type f -iname '*.mp3' **,** -iname '*.mp4' -mtime +10 -exec rm {} \;
```
watch out the ',' between the two expressions of 'iname' and the ' ' that enclose the extensions. That way you avoid misinterpretation from the shell. 
FYI this works for  two expressions only...

EDIT: For the above example you can use :
**-iname '*.mp[1-4]'**

that way you can have every combination you want, and here in particular:
*.mp1 *.mp2 *.mp3 *.mp4
Do the same for other extensions you want (for letters you can do the same e.g. [a-d] *.mpa *.mpb *.mpc *.mpd)!

Regards!

---

### Post by lambono on 2008-04-16
Thats great.
Thanks for the help!

---

