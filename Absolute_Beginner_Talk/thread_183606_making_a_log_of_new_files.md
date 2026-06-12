---
title: "making a log of new files?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by phantomx09 on 2006-05-28
Hello,
I'm looking to make a "status" page that will display the newest files added to specific folders on my server. This way other users on the network can see what has been added. I thought that the best way to do this would be to write something that creates a log. The problem is I can't find anything useful on creating custom logs. I'm also having trouble finding a way to list the newest files since, from what I understand, linux doesn't log creation dates. Does anyone have any ideas? Thanks in advance.

---

### Post by kingmonkey on 2006-05-28
something like:
```

find /* -mmin 60 > log.log

```
look at the below for more details:
```

man ls
man find

```

---

