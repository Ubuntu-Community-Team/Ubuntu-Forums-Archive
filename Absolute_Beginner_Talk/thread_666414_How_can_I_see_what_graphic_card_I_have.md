---
title: "How can I see what graphic card I have?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Masterpooboo on 2008-01-13
Why is it important and what do I do once I know. I have compiz already and it seems to work fine. I tried installing an animated background and things went a little haywire. I'm thinking it might be the graphic card. There seems to be a lot of discussion about them in here.

I am running Ubuntu 7.04 and have a dell latitude D420 Laptop.

Thanks, Masterpooboo

---

### Post by taurus on 2008-01-13
Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by sisco311 on 2008-01-13
or
```
lshw -class display
```

---

