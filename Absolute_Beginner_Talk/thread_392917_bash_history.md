---
title: "bash history"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Andruk Tatum on 2007-03-25
I feel really stupid for asking this, but:

Is there a way that i can get my console to remember my history?  So when i press the up button, it goes to the last command (and so on)?  is this an option somewhere?  It works for one user, but not another.

---

### Post by eljalill on 2007-03-25
So you mean, the arrow up key brings up the last used commands for one user, but not for the other?
What is the difference between the two users? Are they in any different groups or so?

---

### Post by scxtt on 2007-03-25
what shell is the non-working-history user using?  (as that user) type echo $SHELL ...

---

### Post by highneko on 2007-03-25
Here's what I know about history:
```
#Location of the history file:
foo@bar:~$ echo "$HISTFILE"
/home/foo/.bash_history

#Another way to search bash history:
foo@bar:~$ grep "string" "$HISTFILE"
A string in a history file

#Size in lines allowed in the history file:
foo@bar:~$ echo "$HISTSIZE"
500
```

---

