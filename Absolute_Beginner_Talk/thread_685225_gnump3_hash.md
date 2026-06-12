---
title: "gnump3 hash"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by tava0002 on 2008-02-02
I have streaming working with gnump3d and password authentication, I don't like the plain text password but I can't get the hash to work.

I generate the hash like this

```
echo -n 'username:GNUMP3d:password' | md5sum
```

In the .password file I have: username:hash

Then I restart gnump3d like this

```
 sudo /etc/init.d/gnump3d restart
```

but I am unable to log in, any ideas?  Like I said, it works with plain text password.

---

### Post by tava0002 on 2008-02-02
Any ideas?

---

