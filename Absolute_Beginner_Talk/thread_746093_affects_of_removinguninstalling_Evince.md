---
title: "affects of removing/uninstalling Evince"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-04-05
I want to temporarily uninstall the Evince program, so that I can test to see if it is what is causing problems that I am having in printing forms from the Virginia Department of Taxation website.

But when I start to do the removal in Synaptic it says that it is **also** going to remove "**Ubuntu Desktop**".  What is the consequences of doing this ?  

Will removing "Ubuntu Desktop" render my Ubuntu installation unusable (at least from a graphical perspective) ?

Thanks.

---

### Post by zvacet on 2008-04-05
You can safely remov Ubuntu-desktop.It is meta package and it will not hurt your system if you remove it.But,if you one day decide to do upgrade you will have to install that package again.

---

### Post by Oldsoldier2003 on 2008-04-05
> **zvacet said:**
> You can safely remov Ubuntu-desktop.It is meta package and it will not hurt your system if you remove it.But,if you one day decide to do upgrade you will have to install that package again.

good advice. I generally don't worry too much about the Ubuntu desktop, although it is a royal pain in the neck at times. Any one that custom compiles Pidgin will end up removing the desktop anyhow. 

Unfortunately the meta package is filled with fluff that will be reinstalled should you every need to install it again and it messes up your trimmed down installations...

---

### Post by philinux on 2008-04-05
> **wpshooter said:**
> I want to temporarily uninstall the Evince program, so that I can test to see if it is what is causing problems that I am having in printing forms from the Virginia Department of Taxation website.

But when I start to do the removal in Synaptic it says that it is **also** going to remove "**Ubuntu Desktop**".  What is the consequences of doing this ?  

Will removing "Ubuntu Desktop" render my Ubuntu installation unusable (at least from a graphical perspective) ?

Thanks.

Instead why not elaborate your problem.

---

### Post by wpshooter on 2008-04-05
See this thread:

[http://ubuntuforums.org/showthread.php?t=744665](http://ubuntuforums.org/showthread.php?t=744665)

Thanks.

---

### Post by philinux on 2008-04-05
I doubt very much uninstalling evince will achieve anything. 

More likely printer driver maybe

---

### Post by wpshooter on 2008-04-05
> **philinux said:**
> I doubt very much uninstalling evince will achieve anything. 

More likely printer driver maybe

NO, don't think this problem has anything to do with printer driver.

Am suspecting very highly that it is a problem with this EVINCE program.

see:  [https://bugs.launchpad.net/ubuntu/+bug/212017](https://bugs.launchpad.net/ubuntu/+bug/212017)

Thanks.

---

### Post by philinux on 2008-04-06
After reading your bug report I'd uninstall evince then see if the pdf prints ok.

---

