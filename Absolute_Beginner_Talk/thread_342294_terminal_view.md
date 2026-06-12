---
title: "terminal view"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by pafire on 2007-01-19
Whenever I try typing commands in the terminal I all ways get command not found, have I loaded the Ubuntu correctly or am I typing the commands incorrectly.:confused: :confused:

---

### Post by taurus on 2007-01-19
What commands are we talking here?  Try something like these.

```
whoami
ls -la
ls -l
finger
free
uname -a
```

---

### Post by pafire on 2007-01-19
whoami, finger, and free are the only one that worked

---

### Post by taurus on 2007-01-19
There are no outputs for the other three commands at all?

```
ls -la 
ls -l
uname -a
```

---

### Post by philip360 on 2007-01-19
An observation from a newbie: In my first week I could'nt make them work either. I confused ell with one, or capital eye... ex: l, I, 1  they all looked the same to me..Philip:)

---

### Post by taurus on 2007-01-19
That's why we have what we call cut 'n paste.  You cut the commands here with the left button and you paste them to a terminal with the middle button.  Then, no need to type or any typo.

---

### Post by enopepsoo on 2007-01-19
Yeah, you can paste into the terminal window with ctrl + shift + v

it is a lowercase L by the way.  it is short for 'list.'):P

---

### Post by pafire on 2007-01-19
la:  ls:  no such file or directory, 
unname = bash: unname: command not found

---

### Post by taurus on 2007-01-19
> **pafire said:**
> la:  ls:  no such file or directory, 

```
ls -la
```

> unname = bash: unname: command not found

```
uname -a
```

---

### Post by pafire on 2007-01-19
Yes I am able to get those commands to work. How do I access the different directories listed.

---

### Post by taurus on 2007-01-19
You can use cd to change directory.  Then, you can run ls for listing of that directory.  For instance, if you want to change to your Desktop directory and see what's in there (usually your downloaded will go in there as a default), you would do something like these.

```
cd Desktop
ls
```
And if you want to move back, then run

```
cd ..
```

---

