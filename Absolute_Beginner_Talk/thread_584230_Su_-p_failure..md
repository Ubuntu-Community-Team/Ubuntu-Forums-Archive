---
title: "Su -p failure."
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-10-20
```
su: Authentication failure
Sorry.

```

No idea why...I typed in the correct password. I'm trying to install  some sounds by the way...any ideas why this has happened?

---

### Post by llamakc on 2007-10-20
On Ubuntu it's "sudo".

---

### Post by tarchy on 2007-10-20
Ubuntu disagrees :|

```
You must be superuser (su) to run this script. Please also use 'su -p' command when entering the superuser mode in order to preserve your user environment variables.
tarchy@tarchy:~/Desktop/Borealis$ 


```

---

### Post by llamakc on 2007-10-20
> **tarchy said:**
> Ubuntu disagrees :|

```
You must be superuser (su) to run this script. Please also use 'su -p' command when entering the superuser mode in order to preserve your user environment variables.
tarchy@tarchy:~/Desktop/Borealis$ 


```

No, your script that you are trying to run disagrees.

You can "become" root for a limited period of time with:

sudo -i

---

### Post by tarchy on 2007-10-20
You rawk. Thanks.

---

