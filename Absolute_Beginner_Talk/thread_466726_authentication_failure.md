---
title: "authentication failure"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by nonoykevin on 2007-06-07
how can i use my root as a user? when i enter my password after entering this command ($ su), it results to  Authentication failure...is there any ideas?

---

### Post by mcduck on 2007-06-07
su doesn't work, because it's asking for root's password, not yours. But if you want to open a root session in terminal, use 'sudo -i'. Remember to run 'exit' when you are ready ;)

('sudo su' would work also, but 'sudo -i' loads root's environment and settings correctly while 'sudo su' doesn't..)

---

### Post by zvacet on 2007-06-07
if you have second account it is common thing not to be able to use sudo,because you made that account for security reason(not just from outside,it protect you from yourself).if you have just one account(made during installation)you can get admin privileges by typing sudo in front of command
```
sudo apt-get install package_name
```

or you can become root by typing

```
sudo -i
```

---

