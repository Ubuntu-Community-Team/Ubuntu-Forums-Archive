---
title: "sudo not working?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-10-01
I noticed that when I use sudo the machine does not appear to do anything.  So I tried:  

```
sudo cat /var/log/messages > sudo.tst 
```

I was prompted for my password and the file sudo.tst was created but it was empty.  Any ideas?

---

### Post by daller on 2006-10-01
You don't need sudo proviledges for that!

Try without sudo... I don't think it has anything to do with sudo functionality!

Does "sudo init 0" work? :KS

---

