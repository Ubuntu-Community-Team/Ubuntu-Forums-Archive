---
title: "Ventrilo"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by CorranSW on 2007-07-08
Hi i have been trying to set up a ventrilo server on my ubuntu platform..
I followed the instructions on the home page and everything work fine on the first go..
[http://ventrilo.com/setup.php](http://ventrilo.com/setup.php)
Then i accidentally moved some file in the ventrilo directory.. and it got messed up..
So afterwards i deleted the ventrilo folder and tryed again...
At the very end of the setup when prompted to put ./ventrilo_srv in terminal i get an error saying 
no such file or directory??? Whats going on??
Any help will be appreciated..

---

### Post by criz8426 on 2007-07-17
There is an issue noted on the ventrilo forums about an incompatibility with Ubuntu's filesystem (exactly what or why, I don't know).  In any case, it does work for me if I access the ventrilo_srv binary using the full path (ex. criz8426~$ /var/ventrilo/ventrilo_srv ).

---

