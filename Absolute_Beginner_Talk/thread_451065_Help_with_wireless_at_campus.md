---
title: "Help with wireless at campus"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-21
My install of ubuntu went fine and I have wireless access at home just fine. However, on campus I can connect to the access points just fine but can not get online. Normally, with xp, vista and apple, once you launch IE or firefox, a web page loads and asks you to enter your user and pass. After authentication, you are free to surf for as long as you maintain the same IP. However, I tried with ubuntu, it connects, but the credentials page never loads. It just hangs at looking up... Any idea how to get ubuntu to work with the network on campus?

---

### Post by Bachstelze on 2007-05-21
Your network most likely uses some more advanced encryption method than WEP, so using it in Linux might require some work. Can't you just ask the network admin about that ?

---

### Post by jba6511 on 2007-05-21
I doubt it but it is worth a try. I will see if they can get me anywhere. I know they say they only officially support xp and apple OS. Anyone else have any ideas?

---

### Post by Bachstelze on 2007-05-21
I guess we at least need to know what kind of encryption that network uses. When you'll be there, do

```
sudo iwlist eth1 scan
```

and paste what you get. Replace eth1 with the correct interface of course.

---

### Post by jba6511 on 2007-05-21
will do. probably will not be until Thursday and then I will report back.

---

