---
title: "Oracle 10g XE/glibc"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by p252 on 2007-05-11
Ok, I am running Feisty Fawn and I am about to install Oracle 10g Express Edition. Before I install it I am suppose to make sure that I have libaio and glibc installed. In synaptic I can see libaio1 but the only glibc package I see is the documentation. Is it already installed? Is it called something else?

Thank you for your help

---

### Post by octoberdan on 2007-05-11
> **p252 said:**
> Ok, I am running Feisty Fawn and I am about to install Oracle 10g Express Edition. Before I install it I am suppose to make sure that I have libaio and glibc installed. In synaptic I can see libaio1 but the only glibc package I see is the documentation. Is it already installed? Is it called something else? 

Thank you for your help

What tutorial are you following?

glibc used to be a package, but is no longer. I'm not quite sure why...

You can always install libaio1 and try to continue. We can help you if something fails. An error message may even shed some light on the issue

---

### Post by p252 on 2007-05-11
I'm using the install instructions from the oracle web site [http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm](http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm)

---

### Post by p252 on 2007-05-11
Maybe I'll just try to install without and see what happens. . .

---

### Post by Psicolonia on 2007-05-11
yes i've done that a while ago, you just have to install and nothing else. make sure your internet connection is up and it will download whatever he needs.

---

### Post by p252 on 2007-05-11
Well I did it. Installation was a breeze and I must say the Oracle 10g XE runs AWESOME on Ubuntu! Even with the 512 MB RAM I'm currently running (this is just to get the DB developed, it will be moved to a server with more RAM) the DB runs fantastic. Memory management is excellent. Deployment is easy. It also comes with Application Express which is an all in one for building/hosting your web application that interfaces with oracle. The only draw back to it is it only supports http so all authentication is done clear text. You can, however, set up  Apache (something Ubuntu does well too) and use https but that requires a little more work and php programming. So all in all, my thanks to the Ubuntu team yet again for a fantastic OS that servers my needs (and wants :) ).

---

