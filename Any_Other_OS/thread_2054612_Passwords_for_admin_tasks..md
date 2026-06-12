---
title: "Passwords for admin tasks."
date: 2012-09-07
forum: Any Other OS
---

### Post by joey00 on 2012-09-07
I just did a re-install of Mint 13 xfce on a machine that had crashed.

Everything seemed to go ok. I retained the /home directory and allowed the re-formatting of the root area. Swap was untouched.

I now have a nicely running system, with the contents of my desktop exactly as they were.

However, a few programs are missing altogether, but, more seriously, I cannot access update manager, synaptic etc. It doesn't accept the password.

I used the same one in the new install as the old. I can log in, but thats all the password is good for.

Anybody know where the problem is coming from?

---

### Post by Perfect Storm on 2012-09-07
Moved to Other OS/Distro Talk.

---

### Post by sisco311 on 2012-09-07
Make sure that gksu's authentication mode is set to sudo:
```
gksu-properties
```

---

### Post by joey00 on 2012-09-08
> **sisco311 said:**
> Make sure that gksu's authentication mode is set to sudo:
```
gksu-properties
```

Yes it is.

---

