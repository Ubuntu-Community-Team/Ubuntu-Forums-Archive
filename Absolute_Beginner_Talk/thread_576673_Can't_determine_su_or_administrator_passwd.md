---
title: "Can't determine su or administrator passwd"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by pdb7285 on 2007-10-15
How can I change my root, su, or administrator password?

---

### Post by bodhi.zazen on 2007-10-15
The easy way for root access is :

```
sudo -i
```

To set a root password : ```
sudo passwd
```

To lock it again : ```
sudo passwd root -l
```

And the classic link : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

