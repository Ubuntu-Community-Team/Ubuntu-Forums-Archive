---
title: "Help with setting myself as the owner"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Fataltragedy2 on 2007-03-15
How do I set myself as the owner of the computer? I can't copy and paste/edit/delete files in my usr directory and I need to. 

Thanks!

---

### Post by bodhi.zazen on 2007-03-15
You don't ...

Do not change ownership of system files unless you know what you are doing.

Instead use sudo.

From the CLI : ```
sudo cp <file> /usr/
```

Or if you prefer a graphical interface :

In a terminal : ```
gksudo nautilus
```

Whe asked for a password, use your log-in password. You will not see your password in the terminal ...

---

