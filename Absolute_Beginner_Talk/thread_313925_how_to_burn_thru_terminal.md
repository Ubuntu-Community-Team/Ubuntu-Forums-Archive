---
title: "how to burn thru terminal"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by foxmxrcer on 2006-12-06
Hello,
Recently linux crashed on me.. it says its missing libaudiofile.so.0 . if anyone can tell me how to solve that, thats great...but REALY all i NEED to do is get a folder from my desktop burnt onto a disc.  Can someone give me a link to a tutorial or tell me how to do this?](*,) 

Thanks, Jake

---

### Post by daniminas on 2006-12-06
```
> mkisofs -o dani.iso /home/daniel/

> cdrecord -v speed=4 dev=0,0,0 -data dani.iso
```

dev is where is installed your CDRW

---

