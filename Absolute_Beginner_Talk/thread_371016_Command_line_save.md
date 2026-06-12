---
title: "Command line save?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2007-02-26
Very new, gang--but ambitious!

I have the slow internet problem (with Dapper). I've researched the forum and have decided that disabling the ipv6 is my best bet. I'm attempting to follow posted instructions.

By accessing the "aliases" file, via teminal/command line

sudo vi /etc/modprobe.d/aliases

I have changed

alias net-pf-10 ipv6

to

alias net-pf-10 off

I am then instructed to save the file and reboot. How do I save my changes?

Thanks in advance--I look forward to learning more!

---

### Post by taurus on 2007-02-26
Press the Esc key.  Then do

```
:wq!
```

---

### Post by Maestro23 on 2007-02-26
Try using nano as your editor.  Little easier for people new to linux/terminal.

Just a tought.

---

### Post by v8YKxgHe on 2007-02-26
yeah I agree, Nano is nicer than Vi. All you do then is Ctrl+O to save, Ctrl+X to exit :P

---

### Post by jaredssix on 2007-02-26
Thanks for the prompt response!

---

