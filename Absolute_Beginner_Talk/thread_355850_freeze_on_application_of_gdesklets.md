---
title: "freeze on application of gdesklets"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-07
hello.

i installed ubuntu edgy on my ibm thinkpad T21 a couple of days ago and it's been running quite okay. 

today i attempted to install gdesklets from the repository about three times and it always freezes before the administrator password window shows up.

can anyone please help me fix this problem?

thanks in advance.

---

### Post by taurus on 2007-02-07
Try these from a terminal.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gdesklets gdesklets-data
```

---

### Post by shadowboxer_k on 2007-02-07
it worked! thank you!

---

