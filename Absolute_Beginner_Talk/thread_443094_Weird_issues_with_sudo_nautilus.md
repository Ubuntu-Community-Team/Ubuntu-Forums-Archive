---
title: "Weird issues with sudo nautilus"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by KsR on 2007-05-14
hello everyone, 

 A weird problem(bug??) happens whenever I try to open nautilus in a teminal as a super user.  On execution, several nautilus windows pop instead of one.  When open it as a normal user this does not happen.  
Again the problem also occur while I am navigating these folders as root.

Any ideas on what the problem could be?

Oh, and I am currently using Edgy.

---

### Post by Najand on 2007-05-14
Use:
```

gksu nautilus

```
instead of that and try again.

---

### Post by KsR on 2007-05-14
ok right, no problem with that now.  forgot about gksudo :wink: 
first time I saw sudo doing weird results for graphical stuff though  
thanks.

---

