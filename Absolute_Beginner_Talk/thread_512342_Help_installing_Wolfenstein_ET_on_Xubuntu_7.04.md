---
title: "Help installing Wolfenstein: ET on Xubuntu 7.04?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Wolfraptor1 on 2007-07-29
O.K. so I went and downloaded the .run file from their website and I tried all the install commands suggested:


sudo
"your p*****word"
chmod u+x et-linux-2.55.x86.run
./et-linux-2.55.x86.run

didn't work...

sudo
"your p***word"
sh et-linux-2.55.x86.run

again nothing....an error...

Can someone help me fix this, what am I doing wrong?

---

### Post by Bachstelze on 2007-07-29
You musn't run sudo alone but put it before your commands :

```
sudo chmod +x et-linux-2.55.x86.run
sudo ./et-linux-2.55.x86.run
```

---

