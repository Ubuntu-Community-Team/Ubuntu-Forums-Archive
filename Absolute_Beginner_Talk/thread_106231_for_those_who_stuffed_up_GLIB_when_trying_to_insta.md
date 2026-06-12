---
title: "for those who stuffed up GLIB when trying to install GAIM2.0"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by invisage01 on 2005-12-20
Hi there,

Being a linux newbie - i learnt this one the hard way.. 
this is just a post to let people know that if you have done what i've done.. and jumped on slashdot... gone OMG!!!! Gaim 2.0 beta is out!!!! i'd better install the source!!!

but Wait!! it's detected that you didnt have the proper GTK support!!! so youve gone and got the latest GTK libraries... stuffed the whole thing up when you installed GLIB.. All the LD_LIBRARY_PATH needs editing.. your going...ummm !!!

can't work out how to fix it?

easy! just go back to your GLIB source .. 


throw in some:

```
make uninstall
```

this will remove your stuffed up GLIB install.. then just simply go back and follow these instructions...

[http://gaim.sourceforge.net/faq-ssl.php#q14]("http://gaim.sourceforge.net/faq-ssl.php#q14")

--- 

worked fine for me... hope this helps anyone who ran into the same problem as me! 

cheers
i.

---

