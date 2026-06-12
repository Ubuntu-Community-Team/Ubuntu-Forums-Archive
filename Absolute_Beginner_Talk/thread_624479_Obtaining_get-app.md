---
title: "Obtaining get-app"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by jimmy-j on 2007-11-27
I would like to load mysql, but they suggest using "get-app" to do this.  The application "get-app" isn't on the desktop version 7.10 that I installed.  Can I get this application somewhere else?

jimmy-j

---

### Post by jfinkels on 2007-11-27
Read the first link in my signature on installing software in Ubuntu.

To install mysql, type in the terminal:```
sudo aptitude install mysql-server
```

---

### Post by schauerlich on 2007-11-27
I think they meant "apt-get." Try running ```
sudo apt-get install mysql-server
```

---

### Post by jimmy-j on 2007-11-27
You're right, it was apt-get command, and it worked great.  I'm an idiot!  Thanks

---

