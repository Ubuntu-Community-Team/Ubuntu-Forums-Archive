---
title: "Where can we find Ubuntu version #?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by RobbieT on 2006-08-13
This makes me feel like a total noob, but how do I find the version number of the Ubuntu version I'm running? I'm on Dapper, and theoretically have updated to 6.06.1, but where can I see the version number in the program itself?

---

### Post by kostkon on 2006-08-13
The command is

```
lsb_release -a
```

and if you don't get the version you expected, you can get help here at this thread:

[http://ubuntuforums.org/showthread.php?t=234630]("http://ubuntuforums.org/showthread.php?t=234630")

---

### Post by sri on 2006-08-13
main menu > system > about ubuntu

hope tahts what u meant

---

### Post by moma on 2006-08-13
Already told by "kostkon":

[COLOR="Green"] lsb_release --all[/COLOR]
or 
[COLOR="Green"]cat /etc/issue [/COLOR]

---

### Post by RobbieT on 2006-08-13
> **kostkon said:**
> The command is

```
lsb_release -a
```

and if you don't get the version you expected, you can get help here at this thread:

[http://ubuntuforums.org/showthread.php?t=234630]("http://ubuntuforums.org/showthread.php?t=234630")

That worked - thanks!

---

