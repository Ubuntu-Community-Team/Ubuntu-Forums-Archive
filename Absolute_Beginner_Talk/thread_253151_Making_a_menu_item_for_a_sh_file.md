---
title: "Making a menu item for a sh file"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by spyke01 on 2006-09-07
I downloaded Calgoo First draft and got everything setup, the problem is you have to run a shell script to run it, i saw on another site how to make an alias to run it so i did and called it calgoo_start it links to /home/spyke01/Calgoo/start_calgoo.sh 

I tried using alcarte to add a menu item for it using the calgoo_start command but it didnt work, i also tried with the run in terminal box checked, however terminal closes after running the command which in turn shuts down calgoo, any ideas?

---

### Post by jordanmthomas on 2006-09-07
make the executable line in the shortcut read:
```
sh /home/spyke01/Calgoo/start_calgoo.sh
```

---

### Post by spyke01 on 2006-09-07
> **jordanmthomas said:**
> make the executable line in the shortcut read:
```
sh /home/spyke01/Calgoo/start_calgoo.sh
```

Thanks jordan it worked perfect :KS

---

### Post by jordanmthomas on 2006-09-07
no problem

---

