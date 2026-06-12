---
title: "using 'cp' in the command line"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ghandi69_ on 2007-05-31
Here is a quicky...


Say I want to copy the folder Temp in my home directory to somewhere else.. I would do...

sudo cp /home/tony/Temp /usr/lib/win32

or something like that...

but lets say I want to copy all of the 70 files located within /home/tony/Temp in that location.... but not the Temp directory itself... how do I do this???

---

### Post by Seti on 2007-05-31
```

cp /home/tony/Temp* /usr/lib/win32

```

---

### Post by mozetti on 2007-05-31
Since you're looking for a quick answer I'll give it a shot, but I'm not at home with my linux machine to try it out.I *think* that you just need to use the wildcard "*" to do it.
```
sudo cp /home/tony/Temp/* /usr/lib/win32/
```

---

### Post by ghandi69_ on 2007-05-31
Thanks a lot fellas, worked like a charm.

---

