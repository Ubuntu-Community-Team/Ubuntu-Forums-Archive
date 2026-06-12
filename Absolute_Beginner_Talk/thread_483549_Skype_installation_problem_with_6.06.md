---
title: "Skype installation problem with 6.06"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by absolutnoob on 2007-06-24
I had downloaded skype 1.4 (The 7.04 package) beta on my 6.06 and wants to install it. It says that require libasound2 to be installed, but the funny thing is that I already had that installed. So can Anyone tell me how to do? Thanks!

---

### Post by wormser on 2007-06-24
Applications> Accessories> Terminal

```
sudo apt-get install libasound2
```

---

### Post by dmizer on 2007-06-24
libasound2 has dependency problems that are not resovable in dapper or edgy at the moment.  the libasound2 you have installed in dapper is the wrong version and will not work with skype*.

simply put ... skype 1.4 beta for linux is feisty only.

i've been looking for a workaround on this, but i've yet to find anything that doesn't potentially destroy your ubuntu install.






*that's not entirely true though.  it does actually work with libasound2 in edgy (don't know about dapper), but you'll be forced to run your system with broken packages ... not good.

---

