---
title: "Configuring powernowd"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by BrianB on 2005-09-24
I'm having trouble configuring powernowd, i've created the file /etc/default/powernowd and entered my options like so```
OPTIONS="-q -m 0 -u 90"
``` and it doesn't seem to do anything? I've done```
powernowd -v
``` in terminal and it says powernowd is still configured with the default options. Anybody know what's wrong?

---

### Post by mo_x on 2005-09-24
powernowd has to be restarted with:

sudo /etc/init.d/powernowd restart

---

### Post by BrianB on 2005-09-26
I've tried it and it makes no difference.

---

### Post by BrianB on 2005-09-27
Anybody?

---

### Post by mo_x on 2005-09-28
The options are set by the init script not when you start the powernowd from the console. You can check the options with:
```
ps -ef | grep powernowd
```

---

### Post by BrianB on 2005-09-29
I've done that and it shows the options I entered but is that not just showing what it says in /etc/default/powernowd? And I'm pretty sure its not working anyway as when cpu usage goes over 80% it jumps to the full 2.80Ghz instead of increasing by 1 step .

---

