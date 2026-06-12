---
title: "Dosbox mount c:  code"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-07
Below is the original post that I found.


```

i don't know about the pause thing. but to make it automatically mount C: 

you need to create a file called ".dosboxrc" in "/home/<username>/.dosbox/"

this stores configuration information for dosbox and is automatically loaded at startup.

add this to the file
Code:

[autoexec]
 # Lines in this section will be run at startup.
 @echo off
 mount C /home/lala/cai
 C:
 @echo on

then you will be put in C: when you start up.

```


my question is  " .dosboxrc " a file or directory?

if so what is the " [autoexec ] in the code do ?

When I start dosbox i'm in the Z: drive not the C:


The code I add to  .dosboxrc  is as follows:

```

[autoexec]
 # Lines in this section will be run at startup.
 @echo off
 mount C /home/kent
 C:
 @echo on 
```

---

### Post by kent41 on 2006-10-07
I found another post and it works.

Thanks

www.ubuntuforums.org/showthread.php?t=171970&highlight=dosbox+mount[/url]

---

### Post by oyvindaa on 2006-12-18
I'm supposed to type

```

mount c /home/username/dosgames

c:

```

but I can't find how to type the : inside dosbox (This is a laptop).

Anyone know?

---

