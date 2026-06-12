---
title: "Help! I broke my desktop!!"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-10
So I was trying to be smart(fail) and save resources by removing compiz, because I didn't use effects anymore. So I went into synoptics and removed everything with the word compiz in it. Now I have no way to close, minimize, or enlarge windows and can't even take screenshots. How can I fix this? :confused:

Thanks for your time and patience.

---

### Post by jken146 on 2008-01-10
Press Alt+F2 and type ```
metacity --replace
```

---

### Post by 449 on 2008-01-10
Thanks you're a life saver!

---

### Post by barbedsaber on 2008-01-10
could you please mark this thread as solved, instructions in my sig.

---

### Post by 449 on 2008-01-10
Yes, will do. 

How do I make it so I don't do that upon restart?

---

### Post by perlluver on 2008-01-10
Try gtk-window-decorator --replace.

---

### Post by dinostabOMG on 2008-01-10
Go to system->preferences->sessions. If compiz or emerald is checked there, uncheck them. Click Add. 
Name: Metacity 
Command: metacity --replace
Comment: Whatever you want.

---

### Post by 449 on 2008-01-10
> **dinostabOMG said:**
> Go to system->preferences->sessions. If compiz or emerald is checked there, uncheck them. Click Add. 
Name: Metacity 
Command: metacity --replace
Comment: Whatever you want.

I thought this would do it ,but it didn't.

---

### Post by ubuntu-freak on 2008-01-10
You should've just turned compiz off by going to system>preferences>appearances then the effects tab.
 
Nathan

---

### Post by 449 on 2008-01-10
> **reassuringlyoffensive said:**
> You should've just turned compiz off by going to system>preferences>appearances then the effects tab.
 
Nathan

Thanks...

---

