---
title: "How do I log in as root?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-11-25
Hey!
I'm not sure how to log in as root any suggestions?
When I get into the login screen and type in root and then my pass it doesn't work. Is root called something else like super user?
I know th pass is right because it is the same as my normal user.

---

### Post by 5-HT on 2006-11-25
Please refer to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for all the answers.

---

### Post by Linux&amp;Lizards on 2006-11-25
Thanks!
So I guess the root account is disabled by default eh?

---

### Post by junglepeanut on 2006-11-25
sudo -i
sudo su
sudo -s

sudo -s -H

Be careful read
read man sudo

---

### Post by 5-HT on 2006-11-26
> **Linux&Lizards said:**
> Thanks!
So I guess the root account is disabled by default eh?

NP. Yup, the root account is locked by default but can easily be activated-- though it's not really necessary thanks to Ubuntu's reliance on sudo.

---

### Post by Linux&amp;Lizards on 2006-11-26
> **junglepeanut said:**
> sudo -i
sudo su
sudo -s

sudo -s -H

Be careful read
read man sudo

what d you mean read man sudo?

---

### Post by taurus on 2006-11-26
```
man sudo
```
means look at the manpage for sudo!!!

---

