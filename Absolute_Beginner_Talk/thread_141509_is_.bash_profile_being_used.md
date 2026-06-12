---
title: "is .bash_profile being used?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-03-08
I've created ~/bin directory for my own binaries & scripts. Dapper's
.bash_profile file seems to include magic which would append bin 
directory on my PATH variable, but it never happens.

~/bin directory is on PATH if I do
```

. ~/.bash_profile && echo $PATH

```

does gnome-terminal care about this configuration file at all?

---

### Post by kaamos on 2006-03-08
Gnome terminal is not a login terminal, and so it uses ~/.bashrc if I remember correctly.

---

### Post by mlind on 2006-03-08
yeah, you're right. I've should have read the man page first.
I guess I'll just copy the relevant part to my .bashrc file.

---

