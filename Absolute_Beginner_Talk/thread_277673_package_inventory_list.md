---
title: "package inventory list?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-15
Is there a command I can type that will get me a list of all the packages installed on the system or maybe I could type in a command to see if a specific package is installed. This is a frequent need of mine and I hate having to load synaptic just to see what's installed...

---

### Post by jwbirdsong on 2006-10-15
Do you mean like
```
dpkg --get-selections
```
It CAN give a long list so you may want to pipe it into a file or use the less pipe

---

### Post by aysiu on 2006-10-15
```
dpkg -l
```

---

