---
title: "[SOLVED] I want to remove all Thumbs.db files."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Masoris on 2008-02-05
I want to remove all Thumbs.db files on my PC. So I found a command on google. That is;
```
$ find /home/user -name Thumbs.db -ok rm -f {} \;
```
But it doesn't works, As I know that "rm -f" means delete it without prompt, but it doesn't works. when I run this command, it ask me if I want to remove Thumbs.db file. So I should input 'y' for each file.

---

### Post by kpkeerthi on 2008-02-05
```

$ find /home/user -name Thumbs.db **[COLOR="Red"]-exec[/COLOR]** rm {} \;

```

---

### Post by Masoris on 2008-02-05
> **kpkeerthi said:**
> ```

$ find /home/user -name Thumbs.db **[COLOR="Red"]-exec[/COLOR]** rm {} \;

```
It works. Thank you :)

---

### Post by Joeb454 on 2008-02-05
Glad you found your solution :) Any chance of marking the thread as solved? it's in thread tools near the top of this page. Thanks!

---

