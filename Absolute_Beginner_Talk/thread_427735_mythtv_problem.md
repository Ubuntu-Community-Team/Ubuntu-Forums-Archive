---
title: "mythtv problem"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by didijeeeke on 2007-04-29
hi ,

I have set up mythtv on my main desktop it works fine no problems.
But now i want to make use of the mythtv backend / frontend system so i can watch tv on my other computer.

I installed knopmyth on the other computer and entered the backend ip (my desktop ip) somewhere in those way to large config menus.

When i start the frontend on knopmyth i can see my recordings but as soon i try to watch tv or watch a recorded show i see a black screen for 1 second and then the mythtv menu again weird. I don't get any debug of this problem when i run it in terminal.

Any idea ?

---

### Post by mrpaco on 2007-04-30
I had the same problem with knoppmyth.  Being a MythTV noob, I installed MythDora and all is well

---

### Post by superm1 on 2007-04-30
On your ubuntu system, you will need to open up mythtv-setup and make sure you put in your ip address for the computer rather than the 127.0.0.1 that is there by default.  Also, make sure this address is either static, or that dhcp consistently hands out this address to your computer or you will encounter bad troubles.

---

