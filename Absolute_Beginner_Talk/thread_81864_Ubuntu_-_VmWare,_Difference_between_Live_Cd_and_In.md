---
title: "Ubuntu - VmWare, Difference between Live Cd and Install??"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by ir1shm1ike on 2005-10-25
I have Windows Xp Sp1 and I am running VmWare 5. I tried installing Ubuntu Install Cd and after the install it keeps bringing me to a command prompt. Asking me to login. So I login and enter my password and it says I have new mail and is at a command prompt. I'm not sure why it doesn't get to a desktop, I scrolled through posts and I am using a IDE Drive and also have it set to LSI Logic.  So after I re-installed it a few times, I figured I would try the Live Cd and the Live Cd works well. I ran it through the VmWare and it works and I am up and running with a desktop. Any suggestions why the other one isn't working??

---

### Post by vontez on 2005-10-25
After you login and get to the command prompt, type

```
startx
```

Post any error messages you get if this doesn't start Gnome.  If it does start Gnome, then it is just a matter of setting your default run level.

---

### Post by ir1shm1ike on 2005-10-25
I typed start x after I logged in at the command prompt. It came back and says

-bash: startx: command not found

---

