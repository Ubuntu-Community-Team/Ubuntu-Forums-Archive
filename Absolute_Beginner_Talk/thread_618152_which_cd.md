---
title: "which cd"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by everest on 2007-11-20
why does 'which ls' return the answer /bin/ls but 'which cd' doesn't
return any answer?

---

### Post by PointyWombat on 2007-11-20
It's because 'cd' is a built-in bash command, and 'ls' is not. man bash-builtins for more info.

---

