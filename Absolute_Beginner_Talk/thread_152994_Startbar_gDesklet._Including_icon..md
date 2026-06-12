---
title: "Startbar gDesklet. Including icon."
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by dunomous on 2006-03-31
There is no error or problem with either gDesklet (being the most up to date, I believe. 0.35) or startbar (being .30 I think). 

However, when I want to add a new Starter, such as something like Netbeans. I do not know which command to write (ex. Home's is Nautilus --no-desktop). Along side of that, I would, of course, like the icon to be included as well, seeing as how a bunch of question marks is no fun indeed. [-( 

This forum is much to be praised for, thank you guys so much.

---

### Post by Perfect Storm on 2006-03-31
If the application you want in starterbar came without any icon(s) you have to find or use a custom icon. 

Usually you can find application launchers in /usr/bin so look there if you can find netbeans. If it aren't there try with
```
whereis netbeans
```

---

### Post by dunomous on 2006-03-31
what about the code to enter

---

### Post by Perfect Storm on 2006-03-31
As the same way you launch it eg. from the terminal.

---

### Post by dunomous on 2006-03-31
k. So when it says 

```

Netbeans:
user@home:~$

```

what does that mean?

---

### Post by Perfect Storm on 2006-03-31
Try with the command

```
netbeans &
```

Linux is case sensitive.

---

### Post by dunomous on 2006-03-31
hmm, gives me this:

```

user@home:~$ whereis netbeans &
[1] 8624
user@home:~$ netbeans:

```

---

### Post by Perfect Storm on 2006-03-31
Sorry meant that you run
```
netbeans &
```
in the terminal as it should start the application

not with whereis, my fault.

---

### Post by dunomous on 2006-03-31
hmm, still the same response.

---

### Post by Perfect Storm on 2006-03-31
How did you install netbeans? You might check this: [http://www.cs.wcupa.edu/~rkline/netbeans-lin.html](http://www.cs.wcupa.edu/~rkline/netbeans-lin.html) under NetBeans Installation section.

---

### Post by dunomous on 2006-03-31
Ah, I found it. However when I want to select the .png for it's icon, it does not allow it to be selected. It's installed and located in my user folder. I don't see the problem.

---

### Post by Perfect Storm on 2006-03-31
Just browse to the point where the icon is and press ok. Then try again. It's a bug.

---

### Post by dunomous on 2006-03-31
eh, I just copied the file after trying what you said. Same affect. Thanks so much!

---

