---
title: "Mac Mini Fan running at full speed all the time."
date: 2008-12-07
forum: Apple Hardware Users
---

### Post by wizardspade on 2008-12-07
I am running the newest version of ubuntu 8.10 intrep.
My fan is loud as beastly tower.
Is there any way to fix this?

---

### Post by tiresia on 2008-12-07
Mac Mini PPC or Intel?

---

### Post by wizardspade on 2008-12-07
Its a dual core intel 2.0
Fan runs normal under leopard

---

### Post by cyberdork33 on 2008-12-07
is the applesmc module loaded?

---

### Post by wizardspade on 2008-12-07
lsmod says nope its not loaded,

where should I add modprobe applesmc, so that it starts at boot?

---

### Post by wizardspade on 2008-12-08
Solved.

---

### Post by knicksfan77 on 2008-12-08
Cooling has always been a MAC issue.  Are you using your machine in a cool environment? Even body heat can contribute to over heating

---

### Post by cyberdork33 on 2008-12-08
> **wizardspade said:**
> Solved.

if you solve a problem, you should make sure the solution is posted so that others can use the information. You should also mark the thread as solved from the thread tools menu at the top of the page.

did you add it to /etc/modules ?

---

