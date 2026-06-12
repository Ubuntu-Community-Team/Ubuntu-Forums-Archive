---
title: "Cant log in as SU"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Chuckmeister on 2007-02-05
Hi :) I am trying to install some software that requires SU access to unpack and install. When I start up a terminal, type SU and put in my password I get the following line....

su: Authentication failure
Sorry.

The password I am entering is correct, it just wont let me in. Can anyone suggest why or a solution to why I cant get admin rights. I can use sudo and the password is correct.

Chuck :)

---

### Post by Hinko on 2007-02-05
use sudo passwd first. Then you can set the password for root (su). After that logging in as su should work.

---

### Post by Chuckmeister on 2007-02-05
Thanks :) The sudo password and the SU password, I'd assumed would be the same.
Is there a sudo command that will reset the SU Password for my account???
 ...Its quite the transition from windows :confused:

---

### Post by hyper_ch on 2007-02-05
su is deactivated by default.. normally you do everything as "sudo" e.g.

```

sudo apt-get install linux-header`uname -r`

```

---

### Post by bapoumba on 2007-02-05
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
Please read. For a basic use, activating root account is NOT recommended.

---

### Post by jd65pl on 2007-02-05
There is no point in using the root account, you can do everything from an admin account using the sudo prefix.

---

