---
title: "[SOLVED] aliasing wont work [UNSOLVED]"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by crazyfuturamanoob on 2008-04-19
I wanted to make a new alias hme, that contains those things:
```

cd /home/arho/HME/hme
./terrained

```
When I tried to make it, that happened:
```

arho@ohra-desktop:~$ alias hme='cd /home/arho/HME/hme' && ./terrained
bash: ./terrained: No such file or directory
arho@ohra-desktop:~$ 

```
But if I run both commands separately,
in different lines, it works.

_How to alias those things into one alias "hme"????_

PS. I have triple-checked that terrained is 
where it should be. I see it in nautilus and console too.

edit: and btw how to edit topic's title?
somehow I managed to edit and add [unsolved] 
there. and now i want to get it off from there

---

### Post by george9233 on 2008-04-19
If terrained is an executable, probably just

alias hme="/home/arho/HME/hme/terrained"

---

### Post by crazyfuturamanoob on 2008-04-19
> **george9233 said:**
> If terrained is an executable, probably just

alias hme="/home/arho/HME/hme/terrained"
"Segmentation fault (core dumped)"
That seems to happen every time
with every command, unless I run the
commands in separate lines.

Because ./terrained is fast to write,
I decide to make just an alias that
goes into that directory. But now 
I don't know how to save alias!
HelP!

---

### Post by unutbu on 2008-04-19
Move the quote to the end of the line:

```
alias hme='cd /home/arho/HME/hme && ./terrained'
```

---

### Post by crazyfuturamanoob on 2008-04-19
IT WORKS!!

but how to save the alias so it will be permanent?

---

### Post by george9233 on 2008-04-19
Add it in ~/.bashrc, save, quit, and type

```
source ~/.bashrc
```

---

### Post by crazyfuturamanoob on 2008-04-19
> **george9233 said:**
> Add it in ~/.bashrc, save, quit, and type

```
source ~/.bashrc
```

what the hell is ~/.bashrc??
I have never heard of that.
where is it?
edit:
I know what is it. just found out MYSELF!

---

### Post by crazyfuturamanoob on 2008-04-19
ok, how to remove aliases then?

---

### Post by george9233 on 2008-04-19
Just remove them in the .bashrc file and do the sourcing again.

This might be useful: [http://www.linux.org/lessons/beginner/l6/lesson6a.html]("http://www.linux.org/lessons/beginner/l6/lesson6a.html")

---

