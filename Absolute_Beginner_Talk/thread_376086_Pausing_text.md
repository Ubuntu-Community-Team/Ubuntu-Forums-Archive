---
title: "Pausing text"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-03-04
How do you make a command output only one screen of data at a time?

In DOS you'd do

```
dir /p /w
```

for example, for 'list out the directory contents, pause each screen, spread them out'

I'm trying to run scanpci at the moment but it's all whizzing by at a rate of knots

---

### Post by annda on 2007-03-04
honestly, i don't know. but you can always save the output of any command to a file and read it at your own pace. for example, you can do that

scanpci > Desktop/name_of_file.txt

and get a nice text file on your desktop. you can do that with any command, too.

---

### Post by ecs_pf5 on 2007-03-04
That's the problem. I haven't got a desktop lol

But that's great, I know how to use vi (that's my only other bit of linux knowledge thus far) so that will get me going so I can read what I need to - thanks :)

[edit] worked great ;)

---

### Post by terrysalmi on 2007-03-04
Have you tried to pipe the command into 'more'?


```
command | more
```

or if it's a file you're viewing

```
more filename
```

---

### Post by mcduck on 2007-03-04
> **terrysalmi said:**
> Have you tried to pipe the command into 'more'?


```
command | more
```

or if it's a file you're viewing

```
more filename
```

Sometimes less is more :D

If you use 'command | less' you can scroll up and down, when more only allows scrolling down (press q to quit less).

---

