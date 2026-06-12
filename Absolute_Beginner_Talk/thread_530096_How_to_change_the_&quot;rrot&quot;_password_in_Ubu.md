---
title: "How to change the &quot;rrot&quot; password in Ubuntu 7.04"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by ozzyprv on 2007-08-20
When installing Ubuntu I was asked to enter a password few times, I did.
Now, I think my root password is too weak, and I am likely to forget it.

I tried to changing using the "User settings" windows. I went root>properties, I set a new password and clicked ok. Password does not change.

Any help?

Thanks.

---

### Post by schorsch on 2007-08-20
Per default there is no password for root in Ubuntu; you work with sudo and your own password. Just take a look [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by ozzyprv on 2007-08-20
So, when I type
gksudo nautilus

the password that I enter is my user's password?

---

### Post by schorsch on 2007-08-20
Yes.

---

### Post by Patrick793 on 2007-08-20
> **ozzyprv said:**
> So, when I type
gksudo nautilus

the password that I enter is my user's password?

Yes. You enter you enter your user's password.

Edit: Lol. Posted at the same time as schorsch.

---

### Post by kerry_s on 2007-08-20
> **ozzyprv said:**
> When installing Ubuntu I was asked to enter a password few times, I did.
Now, I think my root password is too weak, and I am likely to forget it.

I tried to changing using the "User settings" windows. I went root>properties, I set a new password and clicked ok. Password does not change.

Any help?

Thanks.


```
sudo passwd root
```

---

### Post by jordanmthomas on 2007-08-20
and since your password is basically as powerful as root's in Ubuntu, you should make yours better too if you feel it's weak.  Just type
```
passwd
```
in a terminal.

---

### Post by ozzyprv on 2007-08-20
Thank you all.

---

### Post by hyper_ch on 2007-08-20
> **kerry_s said:**
> ```
sudo passwd root
```

You shouldn't set a password for root until you know what you are doing.

---

### Post by kerry_s on 2007-08-20
> **hyper_ch said:**
> You shouldn't set a password for root until you know what you are doing.

Like it's not easy to reverse> sudo passwd -l root
what do you know all good again, there's no reason he can't do what he wants, ya live ya learn. peace.

---

