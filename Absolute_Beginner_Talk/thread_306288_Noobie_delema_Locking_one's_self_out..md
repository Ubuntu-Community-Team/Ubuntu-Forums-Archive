---
title: "Noobie delema: Locking one's self out."
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by drewu on 2006-11-24
Hello forums.

I just made it so that the user couldn't do administrative tasks and have locked myself out! I had thought I could log in as root to do administrative tasks but was mistaken. Is there any way I could log in as root and change it back? Shouldn't there be a safe guard for that? I feel noobish.

---

### Post by taurus on 2006-11-24
How did you log yourself out!  If you can describe that a little more, perhaps there is an easy solution to fix it.

Otherwise, try to boot into recovery mode from GRUB menu and at the prompt, change the password for the user again, assuming it's called drewu...

```
passwd drewu
```

---

### Post by aysiu on 2006-11-24
This may help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by mackyman on 2006-11-25
Welcome to the club!

I have done that myself, and thought I was the only one who could possible do it with my clumsiness ;)

The article that aysiu posted should work perfectly, that was how I solved it. Only that I didn't know that you got root permissions with the recovery mode, so I used a old gentoo live cd (I had borrowed out my ubuntu one, stupid me).

---

### Post by drewu on 2006-11-25
Well thanks guys. I need to get ahold of that root password (left it on a paper somewere..) to try it. Sure it will work. Thanks!


P.S. This is actualy my mom's computer that I have set up for her. I would have just reinstalled ages ago if it weren't for some data she needed. Kinda funny how we 'help' our family, eh? I could just use a live cd then, right mackyman? I will try that. Thanks for your help everyone!

---

