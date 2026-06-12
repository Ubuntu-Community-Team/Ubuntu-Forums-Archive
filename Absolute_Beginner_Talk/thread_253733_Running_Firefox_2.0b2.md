---
title: "Running Firefox 2.0b2"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-09-08
Is there a way I can disable/remove firefox 1.5.05 from my system and still keep all the dependant programs running such as java, yelp, etc...

---

### Post by zxee on 2006-09-08
Maybe. You could get/enable the repos for edgy knot2 and then upgrade. Firefox. 2.0b2 is default for knot2. I don't know how advisable that is. After you upgraded FF you would obviously want to comment out the edgy repos. 
 You could have apt-get or your package manager just download the files or start the upgrade and see what it wants to install/remove. I don't want to suggest anything that will mess up your system, and maybe I have so please be careful.

---

### Post by alienexplorers on 2006-09-08
Thanks for the info.  Have been getting 2.0b2 from the mozilla site each and every day.  I am part of the Beta Testing the new version.  Wanted to delete Firefox 1.5.05 from ubuntu, but it also deletes a lot of other stuff I don't want deleted.

---

### Post by kerry_s on 2006-09-09
Here's what i do. As root go to /usr/lib and find the firefox folder rename it to firefox.old, now put the new folder for firefox 2b2 there and it will use the new firefox as if it had all ways been there. If you have problems down the line just rename the old firefox back.

---

