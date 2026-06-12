---
title: "Samba n00b"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-05-11
hey guys, i just got samba to work.

someone help me set it up??

im  a real n00b at networking

i already have a network with all my XP machines, i just gotta get my Ubuntu machine in there.

---

### Post by xthund3rh3adx on 2007-05-11
hellooooo

---

### Post by starcraft.man on 2007-05-11
[Presto!]("https://help.ubuntu.com/community/SettingUpSamba") I think this is what you want to read, to set up Samba correctly :)

Be a bit patient, only so many of us to go around :p

---

### Post by xthund3rh3adx on 2007-05-11
thanks, i took a look and got a feel for samba, thanks! ^_^

i am looking for a simple .conf file that allows me to connect to my ubuntu machine without a username and password.

It needs to be able to read/write to the whole system ( "share = /" ?)
it needs to be able to connect to my printer connected to my Xp machine, and print to it


Thats about it. 

can someone create it for me??

---

### Post by xthund3rh3adx on 2007-05-11
ok i have one set up, but XP asks me for a username and passoword.....

help??

---

### Post by starcraft.man on 2007-05-11
> **xthund3rh3adx said:**
> ok i have one set up, but XP asks me for a username and passoword.....

help??

I believe should be your current user account, the one thats logged into the computer at the time of sharing... not sure (i have it configured for free access inside my network, so no pass).

---

### Post by xthund3rh3adx on 2007-05-11
thanks, that worked like a charm!

now, how do i share a printer that is connected to my XP printer?

---

### Post by xthund3rh3adx on 2007-05-11
nevermind on that too, guys, thanks so much!!

---

### Post by starcraft.man on 2007-05-11
System > Administration > Printing > Globabl Settings > Share Printers.

I think last time I set it up, they are usually detected across your network. 

More info is available [here,]("https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7") I have separate printers for each comp so was never a big priority for me >.>.

EDIT: Hehe, read further down eh? :p

Have a nice time with Ubuntu, and your most welcome.

---

### Post by xthund3rh3adx on 2007-05-12
hey guys, i have my printers set up ^_^.

BUT! i have a problem. 
I can get to my Ubuntu shares just fine from my XP machine, but i cannot get to my XP shares via Ubuntu machine.

Help??

---

### Post by xthund3rh3adx on 2007-05-12
........bump?

---

