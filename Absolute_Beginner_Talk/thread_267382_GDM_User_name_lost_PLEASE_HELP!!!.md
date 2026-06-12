---
title: "GDM User name lost PLEASE HELP!!!"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Jimmytzin on 2006-09-28
Can someone please help me get the GDM name back on the user list?? I can't use the internet

---

### Post by meng on 2006-09-28
What's the problem, could you explain what happened?

---

### Post by Jimmytzin on 2006-09-28
Sure.. we had a really bad electrical storm and the power went out.. so everything shu off and then when I tried booting it back up I noticed that it failed to load several things and then a blue window came up saying that the GDM user was missing and so I pressed anter and it sent me to the terminal

---

### Post by meng on 2006-09-28
Wow, weird, sorry I don't know about that problem, but at least now you've explained it better someone else should be able to help.

---

### Post by Jimmytzin on 2006-09-28
I really hope so!!!!!

---

### Post by gruffy-06 on 2006-09-28
:confused: :confused: :confused: 

Login to the terminal like you would do on gdm and type:

sudo dpkg-reconfigure -a

Report any problems back here.

--KDE or GNOME? Does it really matter?--

---

### Post by Jimmytzin on 2006-09-28
k BRB!!!

---

### Post by Jimmytzin on 2006-09-28
Sorry if I take a while but the hting is that I partitioned my HD and I have Linux on half of it and windows one the other half and I have to logg out of windows to logg back onto Linux and so on.. but I'll be back in a minute

---

### Post by gruffy-06 on 2006-09-28
Nothing serious.

---

### Post by Jimmytzin on 2006-09-28
ok I typed it in and at first it asked me for a password so I typed in my password and then it said command not found

---

### Post by Jimmytzin on 2006-09-28
I got this 
stopping deferred execution scheduler               fail
chown: <<daemon.daemon>>:invalid user

---

### Post by Buffalo Soldier on 2006-09-28
> **Jimmytzin said:**
> Sure.. we had a really bad electrical storm and the power went out.. so everything shu off and then when I tried booting it back up I noticed that it failed to load several things and then a blue window came up saying that the GDM user was missing and so I pressed anter and it sent me to the terminal

1. what were you doing exactly when the computer shut off? add/deleting any user account? anything that got to do with login or permission?

2. what are the things that fail to load?

---

### Post by gruffy-06 on 2006-09-29
From the looks of this, your Ubuntu installation appears to be broken. You may need to reinstall. Such a pain... :(

---

