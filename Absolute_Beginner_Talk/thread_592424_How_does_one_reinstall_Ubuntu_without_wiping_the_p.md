---
title: "How does one reinstall Ubuntu without wiping the partition?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-10-26
I borked a few features on my install...

---

### Post by forestpixie on 2007-10-26
do you mean you want to do a clean install? - or you trying to keep /home? or something entirely different

---

### Post by Starks on 2007-10-26
I want to preserve /home

---

### Post by forestpixie on 2007-10-26
is it on a separate partition

---

### Post by Starks on 2007-10-26
> **forestpixie said:**
> is it on a separate partition

I'm pretty sure that /home has its own partition.

---

### Post by forestpixie on 2007-10-26
I guess it's not then - I assume you'd know if you did make one. 

2 options that I can see -  if you've data in your /home you want to keep either backup it all up, reinstall and then copy the data back - or [create]("http://www.psychocats.net/ubuntu/separatehome") a /home partition before you reinstall. Although there are probably other options that I don't know

If you do a separate partition you can tell the manual partitioner where you're home is just don't tell it to format that part.

---

### Post by forestpixie on 2007-10-26
```
mount
```

should tell you then if you have

---

### Post by gn2 on 2007-10-26
If you don't have a separate /home partition, here's a how-to for creating one: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
.
Once you've done that succesfully you can re-install using Manual partitioning to keep your /home partition.
.

---

### Post by forestpixie on 2007-10-26
there's a link up on post 6 :) - i do like that psychocat stuff - helped me enormously
guess that's why it get's into sigs!

---

### Post by vexorian on 2007-10-26
Can also go to system\administration\system monitor\File system tab

---

### Post by gn2 on 2007-10-26
> **forestpixie said:**
> there's a link up on post 6 :) - i do like that psychocat stuff - helped me enormously
guess that's why it get's into sigs!

Oops, sorry I missed that. 

Much smaller and neater than my drag and dropped one!

---

