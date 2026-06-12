---
title: "sudo and root password"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-03-12
ok, i found this one thread a long time ago, but now i cant find it.  it helped me change "sudo" so that it will ask for the root password, not my user password. so i changed that setting on my laptop, but not on my desktop.  now it just confuses the hell out out me when switching from my laptop to my desktop.  i'm not sure, but is the file: [/etc/sudoers] ?

i guess my question is:
[LIST]
[*]how do i make it so that "sudo" asks for my root password?
[*]**AND**
[*]how do i make it so that i can make "sudo" ask for my regular users password?
[/LIST]
i want to be able to know how to switch it back and forth should i like one setting better than the other.

---

### Post by taurus on 2007-03-12
You shouldn't modify /etc/sudoers at all if you're not sure what you are doing.  Just use sudo on both systems then.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

