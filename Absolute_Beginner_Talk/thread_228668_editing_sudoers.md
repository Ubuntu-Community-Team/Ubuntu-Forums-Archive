---
title: "editing sudoers"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by robek on 2006-08-03
I wanted to create launcher for the program I use to connect to AOL
so I've put somthing like this in sudoers:
robek   ALL = NOPASSWD: /usr/sbin/penggy

is this the correct way?
because it still asks me for the password
whe i type sudo penggy or sudo /usr/sbin/penggy

---

### Post by slakkie on 2006-08-03
Try the following:
```

robek  ALL = (ALL) NOPASSWD: /usr/sbin/penggy

```

This should make it work.

---

### Post by robek on 2006-08-03
ok I changed it to
> robek   ALL = (ALL) NOPASSWD: /usr/sbin/penggy
still asks for the password...

---

### Post by robek on 2006-08-03
Im getting better at solving my own problems ;)

as it says in man sudoers
> When multiple entries match for a user, they are applied in order.
       Where there are conflicting values, the last match is used (which is
       not necessarily the most specific match).

so something like this's not going to work as robek is a member of admin group :)
```

# User privilege specification
root    ALL = (ALL) ALL
robek   ALL = NOPASSWD: /usr/sbin/penggy

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by OU812 on 2006-08-04
What if you created a wheel group as described here

[http://www.kernel-panic.org/wiki/GroupWheel](http://www.kernel-panic.org/wiki/GroupWheel)

This way robek would be a member of the wheel group and could sudo, but not be a member of the admin group? Or would that break something else...

john

---

