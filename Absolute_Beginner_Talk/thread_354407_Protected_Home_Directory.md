---
title: "Protected Home Directory"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by iXneonXi on 2007-02-05
Hello, I'm running Xubuntu 6.06.  How do I make it so other users do not have access to my home directory "/home/x" where x is my username?  Right now any other account can see my files.  I do not want this.

---

### Post by taurus on 2007-02-05
```
chmod 700 /home/x
```

---

### Post by iXneonXi on 2007-02-05
Thank you very much.
If I wanted to return it to default what is the command? chmod "?" /home/x

---

### Post by taurus on 2007-02-05
```
chmod 755 /home/x
```

---

### Post by iXneonXi on 2007-02-05
Hide Home Directory?

Thanks again.  Is it possible to hide (as in not shown when viewing /home in the file manager as a normal user other than "x") your home directory (/home/x) to other users?

---

### Post by taurus on 2007-02-06
Sorry but you can't hide x directory under /home.

---

