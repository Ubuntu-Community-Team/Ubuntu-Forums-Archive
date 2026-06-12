---
title: "[SOLVED] apt-get problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Tux.Ice on 2008-01-02
i im having a problem with apt-get, everytime i try to install a package it says there is no install candadate. whats wrong and how can i fix tis?

---

### Post by w4ett on 2008-01-02
> **Tux.Ice said:**
> i im having a problem with apt-get, everytime i try to install a package it says there is no install candadate. whats wrong and how can i fix tis?

Make sure you have enabled the correct repositories. (if "life" is a deb package)

---

### Post by LowSky on 2008-01-02
are you sure the prgrams you trying to install is in the repos?
if it isn't then apt-get wont do anything for you.

have you tried to look through synaptic to see if program is availible?
have you checked off the use of the multiverse and back-port repos?

---

### Post by Tux.Ice on 2008-01-02
ive got universe enabled and i just enabled backports im trying to install - wine,nmap and gparted

---

### Post by Tux.Ice on 2008-01-02
sweet fixed

admin mark this as solved

---

### Post by GMachine_24 on 2008-01-02
Can you please post the command(s) you use and the resultant output? Otherwise it's kind of hard to judge . . .

Something like:

<code>

>sudo apt-get install pixiedust
>no install candidate

</code>

or whatever is really there.

Thank you.

NM.

Glad you found the answer.

---

### Post by meindian523 on 2008-01-02
The problem is already fixed.and you have to mark the thread solved,not any admin.

---

### Post by Cypher on 2008-01-02
Can you show us your /etc/apt/sources and the specific apt-get command you are using?

---

### Post by meindian523 on 2008-01-02
cypher:The problem is already SOLVED!

---

### Post by Tux.Ice on 2008-01-02
ok this is what i did

```
sudo apt-get install gparted
```

it gave me:

package gparted could not be installed: no install candadate found.

so then i enabled backports and universe

and then it worked

---

### Post by Tux.Ice on 2008-01-02
how do i mark it as solved??

---

### Post by meindian523 on 2008-01-02
The link in my sig or the one in LowSky's sig,both point to the same page and it's very clear there.

---

