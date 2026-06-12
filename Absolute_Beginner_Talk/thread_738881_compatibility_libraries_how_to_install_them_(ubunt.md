---
title: "compatibility libraries: how to install them (ubuntu 7.2)"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by fa.ce on 2008-03-29
I've to install compatibility libraries but i cannot find them in add/remove programs ...
where're there ?
how to install them ?

---

### Post by PmDematagoda on 2008-03-29
What compatibility libraries are you talking about?

---

### Post by fa.ce on 2008-03-29
Thanks for the reply, 
i've to install libstdc++.so.5

---

### Post by louieb on 2008-03-29
> **fa.ce said:**
> i've to install libstdc++.so.5
Go to System>Administration>Synaptic
Press the Search button and do a searh on [B]libstdc

[/B]There is not package by that name but there is libstdc++5 and 25 other c++ runtime libraries.

Also just wondering have you installed to package build-essential.

---

### Post by fa.ce on 2008-03-29
> **louieb said:**
> Go to System>Administration>Synaptic
Press the Search button and do a searh on [B]libstdc

[/B]There is not package by that name but there is libstdc++5 and 25 other c++ runtime libraries.

Also just wondering have you installed to package build-essential.
i've done as you said but i continue not to find it ...
package build essential: where's it ? always in Synaptic ?
Thank you very much

---

### Post by PmDematagoda on 2008-03-29
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

