---
title: "Running Firestarter on login"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by PsyberOneZero on 2005-10-07
I'm sure there's some obvious way to do this but I can't find it.  How do I get Firestarter to start-up when I login *without* needing to type in a password.

---

### Post by Perfect Storm on 2005-10-07
Here you go: 
```
sudo gedit /etc/sudoers
``` 

Add in the buttom of thte page: 
<insert your username> ALL= NOPASSWD: /usr/sbin/firestarter 

Then: Systems ---> Preferences ---> Sessions 
Click the startup programs tab. Press 'Add' and write 

sudo firestarter --start-hidden 

Set order to 50

---

