---
title: "reenable compiz and emerald"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-03-23
Ok, so I was using s-video last night and somehow my resolution got messed up.

I went in through xorg-xconfig in the terminal and changed it so it boots up in the right resolution, but somehow now it's not using compiz or emerald. I assume there's an easy way to reenable them rather than uninstalling and reinstalling them. 

Any ideas?

Thanks.

---

### Post by jan quark on 2008-03-23
what is your graphic card?

can you enable the effects going to 
system > appearance > visual effects > normal (extra) ?

---

### Post by dgbearcat on 2008-03-23
> **jan quark said:**
> what is your graphic card?

can you enable the effects going to 
system > appearance > visual effects > normal (extra) ?


well, I'm dumb for not thinking of that, but unfortunately I get "desktop effects could not be enabled"

Any idea why that would be?

---

### Post by dgbearcat on 2008-03-23
never mind, my nvidia driver config stuff got turned off. 

did nvidia-xorgconfig and fixed it.

---

### Post by jan quark on 2008-03-23
it would be nice to know your specs... 
please post the result of  these terminal commands

```
lspci

sudo lshw -C display
```


edit:

good to hear it works again

---

