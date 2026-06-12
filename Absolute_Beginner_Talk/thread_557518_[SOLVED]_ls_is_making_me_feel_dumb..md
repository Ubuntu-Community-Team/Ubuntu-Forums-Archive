---
title: "[SOLVED] ls is making me feel dumb."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by jordanmthomas on 2007-09-22
> Provide the Bash command to find all files with "rw-r--r--" permissions going no deeper than 5 directories deep.  Print the output in "ls -l" format.  Do not use pipes to create the output.


How on earth am I supposed to do this without using pipes?  I have read the man page for ls and it doesn't seem like it's able to do this on its own.

---

### Post by Lord Illidan on 2007-09-22
I'm not sure of the solution myself, but from where did you get this problem? Is it some kind of challenge?

---

### Post by jordanmthomas on 2007-09-22
No, it's a homework question for my Unix class (we use OS X for the class, so that's been fun:  turns out OS X's cp is different than Linux's).

I'm not asking for a full solution (I'm not wanting to cheat) I am just wondering if someone can give a hint as to what to look into other than pipes (which seem to be the obvious solution).

---

### Post by Lord Illidan on 2007-09-22
Well, ls -R will recursively look inside no more than 5 directories (just checked right now)

---

### Post by Dr Small on 2007-09-22
write a bash script to do it :p

---

### Post by Lord Illidan on 2007-09-22
This *might* help..i dunno : [http://www.gnu.org/software/findutils/manual/html_node/find_html/Shell-Pattern-Matching.html](http://www.gnu.org/software/findutils/manual/html_node/find_html/Shell-Pattern-Matching.html)

---

### Post by p_quarles on 2007-09-22
If the assignment is to return *only* files with those permissions, you might find the --hide option interesting.

---

### Post by gmaniac on 2007-09-22
[-X ls isn't the answer.** Try finding another** command :rolleyes:

---

### Post by RomeReactor on 2007-09-22
Hi. Are you absolutely sure you must use the **ls** command for the assignment? I know very little about this, but skimming through it's man page it looks like the **find** command can do what you need.

Just a suggestion...

---

### Post by vambo on 2007-09-22
"find" looks a likely candidate for this.
Have a look at

```
man find
```

---

### Post by p_quarles on 2007-09-22
> **gmaniac said:**
> [-X ls isn't the answer.** Try finding another** command :rolleyes:
Erm, did you read the whole thread?

---

### Post by jordanmthomas on 2007-09-22
Oh, I didn't know find could list only things with certain permissions, so I will be able to do it without pipes.  Thanks.

---

### Post by jordanmthomas on 2007-09-22
For the record, find was what I needed:
```
find . -maxdepth 5 -perm 644 -ls
```

Thanks again...the word ls being in the question tricked me I guess.

---

