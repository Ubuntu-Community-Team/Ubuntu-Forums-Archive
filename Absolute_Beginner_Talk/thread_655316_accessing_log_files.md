---
title: "accessing log files"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by ubiubi on 2008-01-01
How do I access the log file or use the 'V' command

---

### Post by llamakc on 2008-01-01
What V command are you speaking of?

```

ken@llamakc 09:29:19:~$ V
bash: V: command not found

```

Most logs are in /var/log. So cd to there:

```

cd /var/log

```

And you can use "cat" "less" "more" "head" or "tail" to check out the contents (or selected areas). Typically, one can do this:

```

less mail.log

(or)

less /var/log/mail.log

```

---

### Post by nick_h on 2008-01-01
You can also use the log viewer, which can be found under  System->Administration->System Log

---

