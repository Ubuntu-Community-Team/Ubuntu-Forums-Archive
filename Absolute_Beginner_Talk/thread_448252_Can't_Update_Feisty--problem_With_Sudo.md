---
title: "Can't Update Feisty--problem With Sudo??"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by WHICKS on 2007-05-18
When I try to update via the update manager , I can see the updates, but when I try to run the updates, I get the following message:

An error has occured

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Any idea what I can do to rectify this problem...thanks.

A second problem, I tried to download wine and vmplayer from the repository, and I can't find them as being installed.  When I tried to reload them using the sudo command, I again received the above error message.

Thanks in advance.

---

### Post by WHICKS on 2007-05-18
sorry, I mis-configured my search and found my own answer.  If anyone else has this problem
go to the terminal and type the following

sudo dpkg --configure -a


This should work.  Sorry , I am still quite noobish.

---

### Post by echo $USER on 2007-05-18
> **WHICKS said:**
> sorry, I mis-configured my search and found my own answer.  If anyone else has this problem
go to the terminal and type the following

sudo dpkg --configure -a


This should work.  Sorry , I am still quite noobish.

didn't take you long to figure it out

---

### Post by Sef on 2007-05-19
> This should work. Sorry , I am still quite noobish.

That's ok.  We all have made mistakes.   

Thank you for posting your answer.

---

