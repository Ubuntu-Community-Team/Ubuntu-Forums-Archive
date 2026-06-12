---
title: "No dialup internet conection"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by ronee0-1 on 2006-08-20
Installed Dapper (complete noob)modem dials up but fails to make the connection have checked Ip tele. No., username & password all O.K.Have made several attempts. Help me please.](*,)

---

### Post by gargoyle on 2006-08-20
I had similar problem.
I would connect but the connection would drop in about 30 seconds. I was able to tell this was happening because I had an external modem and could see the light lite up then go out.
It turned out that I needed to edit one of the config files. Unfortunately I failed to bookmark the page so I am problems finding it again. If I find it I will post the cure to my problem and maybe yours.

---

### Post by ronee0-1 on 2006-08-22
Thanks for your concern Gargoyle, have solved my problem, for anyone in the same position make sure you have the isp's address after your user name.
For interest I opened a terminal for the first time and used the instructions from "dialup modem how to"this is where you start

     $ sudo pppconfig

 and follow the instructions it's simple

---

### Post by MaximB on 2006-08-22
Gargoyle - if you still have that problem with "dropping" after 30 seconds
you need to
1.configure your network addresses (your ISP dns)
2.right after that with **_no delay_** make the .conf file "read only".

---

