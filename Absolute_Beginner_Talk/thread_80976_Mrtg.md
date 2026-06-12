---
title: "Mrtg"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by herrpoon on 2005-10-23
Hi, I'm having  problems trying to get MRTG to run, I installed it via synaptic but whenever I try and run it, I get the following error:

```
ERROR: Mrtg will most likely not work propperly when the environment
       variable LANG is set to UTF-8. Please run mrtg in an environment
       where this is not the case:

       env LANG=C /usr/bin/mrtg ...
```

Any ideas?

Thanks for any help.

---

### Post by LorenzoD on 2005-10-23
MRTG is telling you that it won't run well in an UTF-8 environment. Ubuntu uses Unicode by default. MRTG is even friendly enough to suggest to you how to start it. I would try exactly that: export LANG=C /usr/bin/mrtg

---

### Post by herrpoon on 2005-10-23
Oops :rolleyes: I should have really tried that before posting!  Now it's just a matter of configuring mrtg!

---

