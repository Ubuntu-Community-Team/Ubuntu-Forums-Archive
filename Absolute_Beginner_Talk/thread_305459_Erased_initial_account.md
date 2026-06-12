---
title: "Erased initial account"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by bubba6 on 2006-11-23
Hi All,

I did something really foolish,](*,)  I deleted my initial account and tried to create a new account in Ubuntu 6.06. I restarted and found out that I could not login into the new account.

I tried login as root in safe mode and tried creating a new account. However, it still doesn't work. The command I used is:

useradd -g root -p [password] -d /home/teo -m teo where teo is the user which I want to create.

Can anyone help me? I looked up several websites and forums but can't seem to find the solution

Thanks

---

### Post by taurus on 2006-11-23
```

useradd -m -G adm,admin teo
passwd teo

```

---

