---
title: "I need to find my gateway address"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by tc105 on 2007-07-08
I am trying to connect another computer to my internet connection, but I can only find my IP and mask using ifconfig, I can't find the gateway address anywhere and I'm really stuck till i have it :s
Thanks anyone :)

---

### Post by fastpakr on 2007-07-08
Right click the connection icon in the taskbar and select 'Connection Information'.  It's the 'default route' listed.

---

### Post by secret_force on 2007-07-09
Hello,

I have the same problem (I would also like to know my default gatewayadress), but i'm using Kubuntu so i don't have an icon i can right-click on. Is there a command in konsole that would show me the same information?

---

### Post by JeSTeR7 on 2007-07-09
type "route" in the terminal (without quotes, of course)

Your gateway should be listed as "default" under the gateway column.

---

