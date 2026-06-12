---
title: "Shutdown Apps through SSH"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-02-14
Is there a way to stop running deamons such as azureus through SSH.
I'm connected trhough SSH to my home pc and its running so slow. I know azureus is the one causing all the slowdown. Sucking too much network bandwidth. 
Is there any way to stop it. shut it down through SSH. Start apps or stop them to run in the background through ssh.

:h34r: Jaygo333 :h34r:

---

### Post by Jaygo333 on 2006-02-14
Any SSH Guru's Please!

:h34r: Jaygo333 :h34r:

---

### Post by tageiru on 2006-02-14
Send a kill signal to the process.

man kill

---

### Post by orbit on 2006-02-14
```
killall java
```

works, but kills all java programs.


Happy killing,
orbit

---

### Post by palomar on 2006-02-14
look with 'top' which process causes the heavy load and then terminate it with 'kill <processID>'.

---

### Post by engla on 2006-02-14
There is a thread for you!
[Howto use the kill command]("http://ubuntuforums.org/showthread.php?t=129692&highlight=howto+kill")

---

