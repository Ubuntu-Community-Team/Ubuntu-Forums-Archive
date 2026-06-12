---
title: "Please explain the &quot;grep&quot; command to me"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by BlueStreak on 2006-07-14
I hear grep tossed around a fair bit and have heard it's a very useful command.

I did "man grep" for some info but didn't really understand it.

Please explain the purpose of this command and its practical uses.

Thanks!

---

### Post by simonn on 2006-07-14
In a nutshell, it searches for text in a file e.g.

```

grep respawn /etc/inittab

```

Will return all the lines containing "respawn" in the file /etc/inittab

---

### Post by jayemef on 2006-07-14
Grep stands for "general regular expression parser." If you aren't familiar with regular expressions, they are a powerful tool to find string patterns within given text. Read wikipedia for more: [http://en.wikipedia.org/wiki/Regular_expression]("http://en.wikipedia.org/wiki/Regular_expression")

---

### Post by BlueStreak on 2006-07-14
Thanks, that's easy!  Now I feel dumb.  I read all the crap about patterns and such in the "man" file and didn't get it.

this should come in handy

---

