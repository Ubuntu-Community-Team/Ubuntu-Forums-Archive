---
title: "Cannot install lrzsz package, please help"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ssharish on 2007-06-17
hello, I have been trying to install lrzsz the supporting package for minicom. But when i search that on Package manager i dont see any package like, i mean there are no package like that.

I tried this command
```

sudo apt-get install lrzsz

```

but it say that i couldnt able to find that package. Does anybody know what is the problem. How will I solve this problem. I need this very soon.

This is what i get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lrzsz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lrzsz has no installation candidate

```

Thank you

ssharish

---

### Post by FleetAdmiral74 on 2007-06-17
If you need it super soon, I would suggest just installing from the source package. Just google their name I would imagine for their website.

---

### Post by qamelian on 2007-06-17
Which version of Ubuntu are you using? There is a lrzsz package in the Feisty repositories (universe).

---

### Post by ssharish on 2007-06-17
Hi guys, thanks for the reply. I am on Ubuntu 6.10 Edgy. 

ssharish

---

### Post by ssharish on 2007-06-17
> **FleetAdmiral74 said:**
> If you need it super soon, I would suggest just installing from the source package. Just google their name I would imagine for their website.

Hi, I even tried installing the lrzsz package manualy, Like you said. I downloaded from their website and installed it. Even still i cant stop this error message. 

The reason i need this because i am working on project related to embedded systems. I have written the code. But without the X and Y modem i cant really deploy the exe file on to the target baord.

This is the error message which I get when lrzsz package is not istalled.
```

Failed transfer Protocal. Press any key to continue

```

Have any one solved this without the package installed. I mean have u tried deploying system without lrzsz.

Please help Thank you

ssharish

---

