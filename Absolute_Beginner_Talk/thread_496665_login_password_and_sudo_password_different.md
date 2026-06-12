---
title: "login password and sudo password different?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by chessercizes on 2007-07-09
Hey guys!

The other day i was thinking, and just out of curiosity, is it possible to make the password you sign in with and the password you give when something needs administrative rights different?

thanks

-parth

---

### Post by aysiu on 2007-07-09
Yes. Use Mepis or some other Linux distribution.

Almost all non-Ubuntu distros come with a separate root password for administrative tasks.

---

### Post by JeSTeR7 on 2007-07-09
Wow, thats very helpful.  I see why you are a mod.

I found this with a quick google search:
> As default Ubuntu has no password set for the root user. To gain root access you have to type in your own user password. This is the password you set for the first user while installing Ubuntu.

To manually set a password for the root user, type in the following in the shell:
sudo passwd

After that you are asked to type in the new root password twice. Finally, your root user has its own password.

[http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)

---

### Post by margaf77 on 2007-07-24
Is there a reason to actually do this? It seems just as secure to me to just choose a strong password for the account used. and if I did this would it change the password when I use sudo or would it allow login as root?

---

### Post by anewguy on 2007-07-24
Please note also that just changing the root password does not give you log on access as root.  There is still one entry in one file (at least in Ubuntu, don't know abou Kubunu).  Not giving that out here is root access is highly discouraged for a new user until they learn more about Linux. :)

---

