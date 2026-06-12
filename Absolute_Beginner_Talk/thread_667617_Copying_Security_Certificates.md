---
title: "Copying Security Certificates"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by cmac1602 on 2008-01-14
Sorry folks, I'm looking to do something that's probably so simple that I will appear a thicko but I just can't crack it:

I have downloaded a security certificate (a .cer file) to me desktop.  I want to copy that into a folder called /usr/lib/ICAClient/keystore/cacerts presumably using terminal.  The folder does exists but how do I instruct terminal in order to copy?

---

### Post by Het Irv on 2008-01-14
I THINK that the command you want is cp
```

Ubuntu@Example sudo cp /home/example/desktop/****.cer /usr/lib/ICAClient/keystore/cacerts
```

The sudo is because you do not have permissions to write to the /usr file by default
Note: Example is to be replaced by your user name.
I THINK this is the correct syntax for this command but let someone else confirm it first. They might even have a better way to do it.

---

