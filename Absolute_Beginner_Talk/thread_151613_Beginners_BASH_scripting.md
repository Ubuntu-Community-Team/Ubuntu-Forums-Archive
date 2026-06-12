---
title: "Beginners BASH scripting"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-03-28
Hi,
If I type a command in a shell. Lets say in 5 mins, its done its stuff and I get the prompt back, then I type something else that works on the output of the first command. That would be fine.

If I just do this in a script :-


command1
Command2

Will command2 not start till command1 completes?
At least thats what I believe, but my fault may be elsewhere.

Just sorta figured out this nautilus-scripts directory, for integrating my own commands.

This is awsome.

Ta
Jeff

---

### Post by halfvolle melk on 2006-03-28
[QUOTE=jethro10]command1
Command2

Will command2 not start till command1 completes?[/QUOTE]
Indeed they will be executed in that order, but if you want the output of command1 to be used as input for command2, you can use 'command1 | command2'.

For instance:
```
cat /path/to/file | grep <something>
```
will let cat read all the lines of file and then grep will only return the lines that have <something> in them.

---

### Post by MartinG on 2006-03-28
If you want command2 not to begin till command1 has exited, you need to use && thus:```
command1 &&
command2
```Or,```
command1 && command2
```

---

### Post by jethro10 on 2006-03-28
Thats what I was after,

th&&nks !

:)

---

### Post by takayuki on 2006-03-28
here's a cool bash scripting site:

[http://www.tldp.org/LDP/abs/html/index.html]("http://www.tldp.org/LDP/abs/html/index.html")

---

