---
title: "Where is the PATH stored?"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by nuttycat on 2006-01-29
I'd like to know where Ubuntu stores the PATH variable. 
I found out from a post on this board that to add to the path I need to do a export PATH=$PATH:<your path>

Can someone tell me where it stores the Path variable?
I looked in /etc/profile but there wasn't any entry in it.
I looked in /<username>/.bashrc ; not there either.

Many Thanks,
Nuttycat

---

### Post by mo_x on 2006-01-29
Bash uses several files depending if it is a login shell or not, see the man page of bash. I think you can add the PATH line at the end of the ~/.bashrc file.

---

### Post by nuttycat on 2006-01-29
UPDATED:
I find that I do have such a file.

Could you tell me the excat syntax of putting the PATH into it.
can i just add PATH=":/usr/local/arm/2.95.3/bin "  to that file?

Thanks,
-Nuttycat

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=nuttycat]UPDATED:
I find that I do have such a file.

Could you tell me the excat syntax of putting the PATH into it.
can i just add PATH=":/usr/local/arm/2.95.3/bin "  to that file?

Thanks,
-Nuttycat[/QUOTE]
You probably want to keep the existing PATHs as well.
```

PATH=$PATH:/usr/local/arm/2.95.3/bin
export PATH

```

---

### Post by nuttycat on 2006-02-12
Thanks,
That solved it.

-Nuttycat

---

