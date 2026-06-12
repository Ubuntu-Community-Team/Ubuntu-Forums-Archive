---
title: "how can i enable unstable repository on Ubuntu 6.06 LTS??"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tmbt on 2007-06-06
Hi guys,
as show in the title.
I would to add to /etc/apt/source.list some unstable repository because i need to install gtk+ 2.10 on my ubuntu but im not able to compile it myself.
I saw this package is avaible  on 7.04 so it should be avaible for dapper too ... how i can i do ?

Thx

---

### Post by zvacet on 2007-06-06
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Click to custom and put link there.I don´t think that Feisty packages will work with Dapper.But I can be wrong.

---

### Post by Kaulbach on 2008-01-15
On any debian based distribution.

The file /etc/apt/apt.conf can be used for this. If it does not already exist create it with admin privelege, gksudo gedit /etc/apt/apt.conf       or sudo nano /etc/apt/apt.conf  
Then add a line:
```
APT::Default-Release "unstable";

```

save and that is all
You do need to do equivelent of sudo apt-get update before installing packages.

---

