---
title: "give user &quot;shutdown -h now&quot; permission"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by edm1 on 2008-04-02
Not sure how you can give you're user permission but why are you logging in as root to do it? Can you not 'sudo' it in Slackware?

---

### Post by bodhi.zazen on 2008-04-02
no, slackware has no sudo

Rather then logging out, open a terminal and enter :

```
su -
```

Enter your root password when asked. Then run the shutdown command.

---

