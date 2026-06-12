---
title: "syncroniseing clock  with ubuntu ?"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by hiptrop on 2005-05-24
i got a little question ... everytime i boot my laptop the clock tries to connect to a ubuntu server to syncronise the clock ! 

well that is no problem but i am not all the time in the internet causing a real long boot when the "clock" tries to connect to ubuntuserver ! and cannto find it because i am not in the internet ....

well ... is there anyway i can turn that option off ? 

many thanks ;)

---

### Post by mtron on 2005-05-24
Open Terminal

sudo chmod -x /etc/init.d/ntpdate

Thats it. 
See [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by Sionide on 2005-05-24
Ah genius! My machine does this EVERY time because I connect through a proxy and it can never find the time servers, aw that's excellent stuff - cheers.

---

### Post by hiptrop on 2005-06-01
ups ! i just see that i forgot to reply ! 

thanks alot !! worked great ! :)

---

