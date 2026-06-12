---
title: "Dependencies"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by spellico on 2007-01-11
I've been trying to install a chess program and keep getting "error: dependencies not satisfiable libc6" . Yet libc6 is installed (in fact all libc6 related are) . Obviously my inexperience. What can I do?

Thanks very much

---

### Post by MkfIbK7a on 2007-01-11
hmmm...
did you try doing
sudo apt-get install libc6
?

---

### Post by Tomosaur on 2007-01-11
First of all is to check whether your game is in the repositories:
```

apt-cache search chess

```
Should list all chess-related stuff. If you find one you want, type:
```

sudo aptitude install <whatever>

```

Doing it this way will satisfy all the dependencies for you.
If you can't find it in the repos, you may need to get it from elsewhere. This is where Ubuntu messes you around, since a lot of the ordinary packages are modified especially for Ubuntu. You may have to also find the 'normal' libc6 off the web and install that too.

---

### Post by spellico on 2007-01-11
thanks. the chess game I want is not in the repos but what I'm getting is still a debian package. what's a normal libc6 (vs. the one already installed)? 

Thanks again.

by the way everything else in ubuntu works great!

---

### Post by tbroderick on 2007-01-11
What game are you installing? What version of Debian was the package built for?

---

### Post by spellico on 2007-01-12
the game is brutal chess - I'm running dapper- Thanks

---

