---
title: "How can I make sure both of my Core 2 Duo T7200 processors are working?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by alphaakenny1 on 2007-01-18
Hey I want to know if Ubuntu is really using both of my processors and if it is using them effectively.  Basically I want to know if I really have Core 2 Duo while using Ubuntu?

---

### Post by tronica on 2007-01-18
go to System-> Administration-> System Monitor. And you should see 2 cpu's. if not you need a kernel that supports dual core.  If you on dapper. than you need the smp kernel. If you on edgy than you need the generic kernel

---

### Post by KaeseEs on 2007-01-18
If you're feeling a little adventurous, you can do this with a terminal command, as well:
```
cat /proc/cpuinfo
```

If both cores are working, you should see entries for 'cpu0' and 'cpu1'.  Now, this program's output is long, so you may want to pipe it to the program 'less', like this:```
cat /proc/cpuinfo | less
```

Finally, there's a way to easily see the state of your cpu(s), memory, network connection, and lots of other stuff, like temperatures, too: a program called 'gkrellm', which is in the repositories.  It stands for 'Gnome KRELL Monitor'.  You can install it via Synaptic, or at the command line, like this:```
sudo aptitude install gkrellm
```

If you want to know what gkrellm looks like, I've attached a screenshot of my desktop running gkrellm; it's on the bottom-right.
Once you've installe gkrellm, open it from Applications -> System Tools .

---

