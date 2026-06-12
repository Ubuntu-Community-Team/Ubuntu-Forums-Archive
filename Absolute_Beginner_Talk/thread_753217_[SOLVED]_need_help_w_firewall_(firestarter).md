---
title: "[SOLVED] need help w/ firewall (firestarter)"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-04-12
here's the senario 

when i go to places --> network --> windows network i can see computer/shared folders etc...

only when firestarter is set to 'stop firewall'

with the firewall i cannot see anything

so how do i configure firestarter to let me see my network?

---

### Post by Inxsible on 2008-04-12
you have to apply the policy to open the ports in Firestarter...

Open Firestarter. Go to the Policy tab, then on the lower window, right click and select 'Add Rule'

Select the appropriate service name like 'NFS' if the network machine is ubuntu or linux or SMB for a windows machine. The port will get filled automatically. Click Ok. 
Then click 'Apply Policy'

---

### Post by myddewji13 on 2008-04-12
thanks that did the trick

---

### Post by Inxsible on 2008-04-12
> **myddewji13 said:**
> thanks that did the trick Glad to know :)

---

