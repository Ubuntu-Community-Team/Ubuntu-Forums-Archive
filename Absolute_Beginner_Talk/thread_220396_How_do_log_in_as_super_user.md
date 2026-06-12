---
title: "How do log in as super user?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-21
I know it has somthing to do with the sudo....but what is the password that i am sopossed to use.

I am reinstalling this as i type, i have created my user account as prompted durring install/setup, I have the password for the user account but when i go to log in as the super user, i dont know what password to use.

Any help would be a benifet....

I like linux already:)
its different.

---

### Post by linear on 2006-07-21
It's that same user password you set up during installation.

---

### Post by mbrang00 on 2006-07-21
ohhh.....

Id like to say that i tried it, but, im not going to say that. Ill take the hit. :)


I do have to say that i really like the fourms setup, as well as the speedy responses i get...

Thanks to all who offer advice and help

Ill try that password after i finish up the reinstallation.

thanks

---

### Post by ewl1217 on 2006-07-21
Ubuntu has the root account locked by default, and instead uses sudo to allow priviledged users to run individual programs as root. For more information on using sudo, or how to enable the root account, see [this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by mbrang00 on 2006-07-21
Thankyou ewl1217, 
that is exactly what i was looking for.


This is my third trial of linux
I started with Fedora, didnt like it,
Played with Knoppix...I like it
Found Ubuntu....Im diggin it alot.

Its a tough learning curve thats for sure, but im in it for the long haul.

---

### Post by aysiu on 2006-07-21
```
sudo -s
``` or ```
gksudo nautilus
```

---

