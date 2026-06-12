---
title: "Your password will expire in X days"
date: 2012-03-13
forum: Any Other OS
---

### Post by ssinxx on 2012-03-13
Hi,

I am running a SUSE OS , when ever i login as root to that machine i am getting this meassage Your password will expire in 10 days...is there a way to disable this option, i don't want to change my password.Please help me out

---

### Post by zombifier25 on 2012-03-13
Does an administrator manage your computer? If so, contact him/her for more detail. If not, type this into your terminal:

sudo chage -I -1 -m 0 -M 99999 -E -1  username

replace username with your account.

---

### Post by ubudog on 2012-03-13
Edit: Zombifier beat me to it while I was posting.  ;)

Do (as root or with sudo): 
```
chage username
```

Press enter for everything except:
Set 'Minimum Password Age' to 0.
Set 'Maximum Password Age' to 99999.
Set 'Password Inactive' to -1.
Set 'Account Expiration Date' to -1.

---

### Post by Perfect Storm on 2012-03-14
Moved to Other OS/Distro Talk.

---

### Post by ssinxx on 2012-03-14
Thanks for the help ):P

---

