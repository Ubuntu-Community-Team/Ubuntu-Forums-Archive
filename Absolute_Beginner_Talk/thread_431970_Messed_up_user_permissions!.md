---
title: "Messed up user permissions!"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by ShakeyJake on 2007-05-03
Hey  everyone.

I (stupidly!) messed around with t he user permissions and managed to render myself  unable to get to the 'user permissions' menu.

I know logging in as root is bad bad bad bad, but I dont see any other way to fix my mistake.

I mean System -> Administration now brings up a tiny menu and theres no 'User permissions' to change i back.

Anyone got any ideas?

---

### Post by taurus on 2007-05-03
Boot into recovery mode from GRUB menu and change your $HOME back to your login name, assuming it's **jake**.

```
chown -R **jake**:**jake** /home/**jake**
ls -la /home
```

---

### Post by ShakeyJake on 2007-05-03
Thanks, but for the first line I get :

chown: ' jack:jack'  :  invalid group

---

### Post by ShakeyJake on 2007-05-03
Ah, and now I  cant log in.

User's $HOME/.dmrc file is being ignored. This prevents the defaul session and language from being saved.  File should be owned by user and have 644  permissions.  User's $HOME directory must be owned  by user  and not writeable by others. 

Thats me told.

---

### Post by taurus on 2007-05-03
If you read my previous post again, it was assuming your login name was jake!  You supposed to replace jake with your actual username.  What is your login name then?

```
id
ls -la /home
```

---

