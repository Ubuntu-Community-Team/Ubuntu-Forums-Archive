---
title: "[SOLVED] Low Latency Audio"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-19
I know Ubuntu Studio has a low latency kernel. I really need something that will focus on the audio when I am multitracking, because right now it is choppy. Any suggestions on what I can use to make my music better?

---

### Post by por100pre1 on 2007-08-19
Did you try the low latency kernel already? Here it works faster than the generic one.

EDIT: Actually you don't need Ubuntu Studio eye candy to use the low latency kernel:

```
sudo aptitude install linux-lowlatency linux-restricted-modules-lowlatency
```

---

### Post by tdrusk on 2007-08-19
I really don't want to drift too far away from my normal Ubuntu. How does it perform?

---

### Post by por100pre1 on 2007-08-19
Added a how-to in the previous post. :) Don't worry, it will only add another kernel, it won't remove the generic one.

---

### Post by tdrusk on 2007-08-19
> **por100pre1 said:**
> Added a how-to in the previous post. :) Don't worry, it will only add another kernel, it won't remove the generic one.

Oh cool. Thanks!

---

### Post by por100pre1 on 2007-08-19
> **fuzzyhair said:**
> Oh cool. Thanks!

Glad to help. Let me know how it works for you.

---

