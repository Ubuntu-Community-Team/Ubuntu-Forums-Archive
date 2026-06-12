---
title: "multiple cores"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by 2manydrugsago on 2008-01-12
My friend uses Vista Ultimate (shudder) and He has a quad core box. I showed me how he could assign specific tasks to specific cores. How do I get Ubuntu 7.10 to do that?

---

### Post by Cypher on 2008-01-12
I don't believe there is a way of assigning specific tasks to specific cores in Linux. Technically speaking you don't want this anyway. The SMP (Symmetric Multi-Processing) Kernel should be smart enough to figure out which core is not doing as much work and take a paritcular task and have that core perform it. If a core were to become overloaded, it should distribute the load to the other cores..

Assigning a task to a specific core means that should the core be busy with something else, with the assignment, the task will get delayed until the core is less busy or free to perform the task rather than getting pushed off to a free core for execution..

---

### Post by Arthur Archnix on 2008-01-12
[http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html](http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html)

But I'd recommend you don't unless you just want to do it for fun, learn how, etc. Otherwise, you're not really doing yourself any performance favours.

---

