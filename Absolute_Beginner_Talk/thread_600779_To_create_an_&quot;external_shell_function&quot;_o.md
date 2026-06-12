---
title: "To create an &quot;external shell function&quot; on a bash file?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-11-02
I noticed that if a bash file, I putted the following code

```
asd() { echo hi ; }
```

And then I tried it

```
 

martin@Linux:~$ gedit hh
martin@Linux:~$ chmod +x hh
martin@Linux:~$ ./hh
martin@Linux:~$ asd
bash: asd: command not found
martin@Linux:~$ 


```

It there any way to do an extern function for htis file?

---

### Post by Fixman on 2007-11-02
er...help please?

---

### Post by Fixman on 2007-11-02
bump.
Or just say "I dunno"

---

### Post by KentS on 2007-11-02
Do
```
source hh
asd
```

---

