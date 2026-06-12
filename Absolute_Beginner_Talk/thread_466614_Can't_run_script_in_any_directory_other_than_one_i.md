---
title: "Can't run script in any directory other than one in my $PATH"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by kmslinux on 2007-06-06
The title says it all. Whenever I try to run a program that's not in my $PATH, as in "./foo", it says this:
```

bash: ./foo: Permission denied
```

Even as root, it says that.

Now when I put foo in /bin, it runs perfectly. (the program foo prints "Foo!")

```
# foo
Foo!
```

Hmmm...

---

### Post by meng on 2007-06-06
Does the program have execute permissions?
ls -l foo
(see if there's an 'x' flag)

---

### Post by kmslinux on 2007-06-06
> **meng said:**
> Does the program have execute permissions?
ls -l foo
(see if there's an 'x' flag)

I knew someone would ask that. The permissions are all set. (chmod 777 foo)

---

### Post by Rocket2DMn on 2007-06-06
Did you "sudo chmod 777 foo"?  You can't change the permissions if you don't own it to begin with.

---

### Post by kmslinux on 2007-06-06
> **Rocket2DMn said:**
> Did you "sudo chmod 777 foo"?  You can't change the permissions if you don't own it to begin with.

Sorry, I failed to mention that **I am root.** (su-ing in terminals)

---

### Post by kidders on 2007-06-07
Hi there,

This may be a dumb suggestion, but is your home (or wherever the script was originally) mounted "noexec" ?

[SIZE=1](Actually, I'm not even sure that would make any difference to a script.)
[/SIZE]

---

### Post by kmslinux on 2007-06-07
> **kidders said:**
> Hi there,

This may be a dumb suggestion, but is your home (or wherever the script was originally) mounted "noexec" ?

[SIZE=1](Actually, I'm not even sure that would make any difference to a script.)
[/SIZE]

DING DING DING!!! We have an answer here. Yes. It was mounted noexec. I'm changing that right now... Done. Foo runs! Thank you kidders!

---

### Post by kidders on 2007-06-07
> **kmslinux said:**
> DING DING DING!!!Lol... to be honest, I thought that one was a bit of a longshot! Glad we managed to pin down the problem for you. :-)

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

### Post by kmslinux on 2007-06-07
> **kidders said:**
> Lol... to be honest, I thought that one was a bit of a longshot! Glad we managed to pin down the problem for you. :-)

I'm such a noob...  :lolflag:

---

