---
title: "Can I remove java5 after installing java6?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-01
Hi,

I previously had Java5 installed and now I've also installed Java6. Can I remove the Java5 packages (sun-java5-bin and sun-java5-jre) if I get these in version 6 or should I just leave Java5 stay along with Java6?

Thanks

---

### Post by starcraft.man on 2007-05-01
I'm pretty sure their installed seperately... they certainly are listed seperately in the repos. Try running this command in terminal:

```
sudo aptitude remove sun-java5-jre sun-java5-bin
```

if it doesn't give you any errors I don't see why there would be any problems.

That was an easy question, have a nice day and don't be shy to ask anything a bit harder :)

---

### Post by zvacet on 2007-05-01
Of course you can.You have latest version and you don´t need previous one anymore.

---

### Post by kilou on 2007-05-01
OK Thanks. I thought that the new version would just update the old one as for all other package updates though....

---

