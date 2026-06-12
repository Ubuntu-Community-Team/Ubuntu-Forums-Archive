---
title: "Upgrading from 6.6 to 8.4"
date: 2008-05-15
forum: Apple Hardware Users
---

### Post by crapple on 2008-05-15
When I try to give upgrade from ubuntu 6.6 to 8.4 it gives me this error.

[IMG]http://img505.imageshack.us/img505/1038/screenshotsk6.png[/IMG]





I am running ubuntu on power pc g4.


Any ideas?

---

### Post by avtolle on 2008-05-15
Looks like you have fallen victim to the apparent midstream change in location of the ppc repositories/mirrors. I don't have my notes on this handy, stream303 among others has posted about this, and there is a thread within the past week or so about how to edit the information about the mirrors, etc., which you hopefully can find. There have been some updates to Update Manager which likely fixes this, but may not have updated yours before you d/l the iso you are using.

Edit: if you are using the upgrade to new distribution button, which it appears you may be, be sure you totally update your current installation before trying it again. The problem may have been fixed recently, and you might not have this problem the next time. 

Edit2: Try this from the terminal, if you haven't already done so:```
sudo aptitude update
``` after editing the /etc/apt/sources.list to reflect the change in sources before trying the dist upgrade. Just a thought.

---

