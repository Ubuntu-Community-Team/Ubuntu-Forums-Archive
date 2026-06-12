---
title: "starting multiple applications with terminal simultaneously."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-06-19
Hi, 
I'm tryinh to wrap my head around some shell scripting. I wondered how I can make to separate applications start in a single bash command.
As it right now, I can get the first to start and then the other, but the first needs to be closed down first.
I don't know how to make them start up at the same time.

code I use:
```
sudo gedit file 1
application X
```

I tried with && but it changed nothing....
Anybody have any suggestions or can point out what quite obvious thing I am missing?
google searches are hell, because I do not know exactly what i need to search for.

---

### Post by bodhi.zazen on 2007-06-19
single &

---

### Post by Ocxic on 2007-06-19
"command &"

---

### Post by JanvL on 2007-06-19
Hi,

try 

application x &

the ampersand put the process in the background.

Here is a very good bash guide
[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

have fun

Jan

---

### Post by bodhi.zazen on 2007-06-19
Single & = run command in background

&& = run second command after the first command completes successfully. If there is an error with the first, the second will not run.

---

### Post by charleseddy on 2007-06-19
x

---

### Post by quinnten83 on 2007-06-19
Tnx guys.
I knew i was making an obvious mistake :)
It works now..

---

