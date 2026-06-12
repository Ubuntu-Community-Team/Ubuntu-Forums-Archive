---
title: "how to comment lines with vi?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-09-16
Hi! I'm getting into the vi editor for a few days, I've read some manuals and tutorials, but I can't realize how to comment say the next 5 (or any number) lines that follows where the cursor is while editing a file with vi. That will be useful while editing code, so I'm sure there's a way to do it.

Could you help me? 

Thank you very much!

---

### Post by reckless2k2 on 2007-09-16
[http://www.washington.edu/computing/unix/vi.html](http://www.washington.edu/computing/unix/vi.html)

---

### Post by fredscripts on 2007-09-16
Thanks for the tutorial...I've read it but I'm still wondering if there's a short cut to insert to the next X lines from where the cursor is an # at the beginning (i.e, comment out X lines), maybe the only way is inserting line by line an # at the beginning...

---

### Post by tvrg on 2007-09-16
you need to find out which are the line numbers but you could use subsitution:

```
:xx,yy s/^/# /
```

where xx is the starting line number and yy is the ending line number
what you are doing then is saying
:  > start a command
xx, yy > run it for line xx to line yy
s/^/# / > replace (s) / the start of the line ^ with a # and a space

---

### Post by tvrg on 2007-09-16
hmm, you could also do the next X lines (had to test it out myself)

```

:.,+5s/^/#/

```

I suppose you can see the logic in that :)

---

### Post by gmaniac on 2007-09-16
nice one. thnx

---

### Post by fredscripts on 2007-09-16
Oh yes! Thank you very much!

---

