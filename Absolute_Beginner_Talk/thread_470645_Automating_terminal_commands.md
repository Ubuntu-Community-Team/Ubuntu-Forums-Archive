---
title: "Automating terminal commands"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-06-11
Hello, I have following question:

I am interested how is it possible to input in terminal two commands in the way that first command starts to execute immediately and the second one waits till the first one is executed and starts only after that. 

How is it possible?

---

### Post by Outrunner on 2007-06-11
Separate them with '&&'

```
sudo aptitude update && sudo aptitude install <program>
```

---

### Post by mlentink on 2007-06-11
If you need to use a certain string of commands more that once, you could turn them into a shell script. 
I'm no guru, but you could look at [this site]("http://www.linuxcommand.org/writing_shell_scripts.php") if you're interested.

---

