---
title: "How to clear Terminal cache?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Harry_Callahan on 2006-09-02
Hello,

is it possibile to eliminate from the terminal the commands I used recently? Pressing the keys UP DOWN you can see commands inserted in the past, I want to clear the the "memory" of the terminal because I generated MD5 passwords, I don't want anyone accessing the terminal and finding out what I've been doing....

Thanks

---

### Post by Rui Pais on 2006-09-02
hi, try
```
 rm .bash_history
```

---

### Post by Harry_Callahan on 2006-09-02
Thanks alot, it works fine! It's necessary to close and re-open the terminal

Thanks again!

---

### Post by Swab on 2006-09-02
history -c

---

### Post by Harry_Callahan on 2006-09-02
Nice! history -c works without re-opening the terminal, It eliminates history immediately.

Thanks to all of this wonderful community!

---

