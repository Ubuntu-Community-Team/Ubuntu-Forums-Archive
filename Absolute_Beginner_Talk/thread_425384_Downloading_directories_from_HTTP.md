---
title: "Downloading directories from HTTP"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by IsKall on 2007-04-27
How do I download directories and its subdirectories + files from a url?

---

### Post by Seisen on 2007-04-27
Are talking about from the terminal?

---

### Post by helphope on 2007-04-27
try wget. It works form shell 
[http://www.gnu.org/software/wget/]("http://www.gnu.org/software/wget/")

---

### Post by agurk on 2007-04-27
Yeah, wget will do the trick if the web server allows directory browsing.
```
wget --help
```

---

### Post by IsKall on 2007-04-27
thanks!

---

