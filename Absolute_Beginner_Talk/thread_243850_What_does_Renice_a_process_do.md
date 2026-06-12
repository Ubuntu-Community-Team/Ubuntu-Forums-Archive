---
title: "What does Renice a process do?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by srusso on 2006-08-25
What does Renice a process do? I have a simple restore running and I think the process died... Am I heading down the right path with this one and can I get the process going again...???

---

### Post by steve.horsley on 2006-08-25
It alters the priority of a running process. To see the details on this, use the command > man renice
(And **q** to quit the manual when you've finished.)

---

### Post by clapper65 on 2006-08-25
All renice does is change the priority of a process.  You can find all the details in the man page. Renice will not restart a dead process.

---

### Post by srusso on 2006-08-25
The status of the simple restore says "Sleeping" and it has 0%cpu. This restore was a /var restore

---

