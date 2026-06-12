---
title: "permissions+terminal"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by strife303 on 2007-06-18
Here's the situation:

My account doesn't have administrator privileges via the system -> administration -> users and groups option, so I can't make changes with my home account. When I disabled admin access I also didn't check the "allow local administrator to log in" option, so I can't log in as root graphically to change this.

Thus said - cannot use alt+f2 nautilus.

What I can do is login with root in the terminal.

What's the command that will let me set my home account back to administrator level so I can access System -> Administration -> Services, etc w/ my home account?

Thanks in advance!!! I'd like to enable apache today but I'm still terminal-retarded from years of windows use.

---

### Post by lambros on 2007-06-18
If your username was "fred", you could use:
```
adduser fred admin
```

That adds your user to the "admin" group, which is what you need to get admin privileges via "sudo" (and its graphical friends).

Hope that helps,
Lambros

---

### Post by strife303 on 2007-06-18
Thanks, problem solved!

---

