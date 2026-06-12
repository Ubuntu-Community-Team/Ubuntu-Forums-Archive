---
title: "nslookup and dig"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by fnkhan on 2008-03-20
when i entered nslookup or dig command there is an error
command not found
plz tell me what can i do i mnew in linux
:confused:

---

### Post by ruy_lopez on 2008-03-20
> **fnkhan said:**
> when i entered nslookup or dig command there is an error
command not found
plz tell me what can i do i mnew in linux
:confused:

Try "which" and "whereis"
```

which dig
whereis dig
which nslookup
whereis nslookup

```

If they don't return any valud results, dig and nslookup probably aren't installed.

If they show the path, use the path to run them:

ie
```

which nslookup
/usr/bin/lookup

/usr/bin/lookup google.com
Name: google.com
Address: 64.233.167.99

```

---

### Post by fnkhan on 2008-03-21
Thanks 4 reply

---

