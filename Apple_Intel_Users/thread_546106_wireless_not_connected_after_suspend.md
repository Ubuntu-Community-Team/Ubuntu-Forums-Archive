---
title: "wireless not connected after suspend"
date: 2007-09-08
forum: Apple Intel Users
---

### Post by albertfc on 2007-09-08
Hi everybody!

I've got a new macbook and almost everything runs good. The only thing thats annoying me is wireless settings. Always, when the machine wakes up after suspend it is not connected to the net and i have to go to wireless settings and reconnect manually. Exits any method to do this task in a automatic way?.

Thanks in advance.

Best regards from Barcelona (and sorry for my english ;) )

---

### Post by albertfc on 2007-09-09
I found the solution:

Append at the end of file "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" this:

ifdown ath0
ifup ath0

Bye!

---

### Post by PaulFXH on 2007-09-09
Hi
I had exactly the same problem and was searching for a solution.
When you say 
> at the end of file "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux"
do you mean immediately before the "exit $RET" on the very last line (line 121 in mine)?

Thanks
Paul

---

### Post by albertfc on 2007-09-10
> **PaulFXH said:**
> 
do you mean immediately before the "exit $RET" on the very last line (line 121 in mine)?


ok, immediately before the "exit $RET" 

Best  regards

---

