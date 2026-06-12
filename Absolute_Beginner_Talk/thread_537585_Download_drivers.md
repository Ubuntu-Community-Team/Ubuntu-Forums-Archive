---
title: "Download drivers"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Andre_3608 on 2007-08-29
Gigabyte S-series motherboard - GA-945GCMX-S2.  Please tell me whence I can download audio drivers - my sound is silent as the grave.  Many thanks...

---

### Post by forestpixie on 2007-08-29
Have you made sure that you haven't got muted channels - I had to turn up 'front' - even though I don't have one-  to get sound working for me.

Open a terminal and type the following in then enter, esc to escape

```
alsamixer
```


If that doesn't work in a terminal type the following - it should tell you which audio card/ onboard you're using - then search the forum for that

```
lspci
```

---

### Post by Andre_3608 on 2007-08-29
No linux drivers are supplied at all - and my internet searches have been unsuccessful.  Please help if you can.

---

### Post by forestpixie on 2007-08-29
so did you actually try any of tyhe prev post - post the output of lspci

---

