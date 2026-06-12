---
title: "Removing Wine Questions"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Gracye on 2006-04-07
OK, so I installed Wine so I could run DVD Decrypter but I realized that I don't want it.  So I've removed Wine, but I have no idea how to remove DVD Decrypter too.  Does it automatically remove when I remove wine?

---

### Post by taurus on 2006-04-07
How did you install DVD Decrypter?  If you installed it with apt-get, then you can use apt-get to remove it.  But if you configured and built it from source, then you need to move the binary from the same directory that you built it!

---

### Post by Gracye on 2006-04-07
I ran the exe file with Wine...

I'm confused sorry! I'm only a 4 day old newbie LOL

---

### Post by trent dillman on 2006-04-07
If you got rid of Wine, delete the .wine folder in your home directory.

```
rm -r ~/.wine
```

---

### Post by Gracye on 2006-04-07
thank you it worked :)

---

### Post by trent dillman on 2006-04-07
No problem!

---

