---
title: "Accessing Ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by blublu on 2007-04-14
[FONT="Century Gothic"]Hi 
From Ubuntu i can access other computers on my network running XP but not the other way around. I login with user/password when prompted but nothing seems to happens[/FONT]

---

### Post by hyper_ch on 2007-04-14
You will have to setup samba and activate shares in it :) Without anything shared they can't access your box with networking :)

---

### Post by BenHines on 2007-04-14
Hi,

I'm having the same problem.  On my ubuntu box, I can view folders that are shared from the XP box.  However, I can't get the opposite to work.  That is, my XP box cannot open folders that are shared from the ubuntu box.   

I am certain that SAMBA is running on the ubuntu box because when I open the "Workgroup Computers" on the XP box, the ubuntu box shows up.  However, when I double-click to open the ubuntu box in a file browser, I am prompted for a username and password.  I go ahead and enter my user id and password for the ubuntu box and it prompts me again (and again and again).  I've done all the standard checks like making sure that the caps lock is not on. I also set the samba password to be the same as my logon password.  All result in the same thing.

Any ideas what I am doing wrong?

Thanks.

---

