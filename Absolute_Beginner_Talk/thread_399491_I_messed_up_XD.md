---
title: "I messed up XD"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mjhasbach on 2007-04-02
Ok...I'm new to linux and I think I just screwed my stuff over. While trying to fix my wireless problem, I was getting "cannot write to directory" and "access denied" errors. So...I went into users and groups and changed my group to root and my home directory to "/" thinking that would help. Wrong. I log out and log back in, and now whenever I try to log in as my user "m" it says that the home directory is invalid...bla, bla, bla. The thing is, root and m are my only users, so if I cant log in as either how am I supposed to log in? Help would be greatly appreciated >_<

---

### Post by justin whitaker on 2007-04-02
> **mjhasbach said:**
> Ok...I'm new to linux and I think I just screwed my stuff over. While trying to fix my wireless problem, I was getting "cannot write to directory" and "access denied" errors. So...I went into users and groups and changed my group to root and my home directory to "/" thinking that would help. Wrong. I log out and log back in, and now whenever I try to log in as my user "m" it says that the home directory is invalid...bla, bla, bla. The thing is, root and m are my only users, so if I cant log in as either how am I supposed to log in? Help would be greatly appreciated >_<

That change basically told the system that you do not have a /home directory. You should be able to log in as root (I hope you enabled login as root in the GDM settings), otherwise, you have to do it via console.

---

### Post by mjhasbach on 2007-04-02
Thats the problem...I only learned about allowing the root to login through GDM after I messed up >_>. How would I go about logging in through the console, and resetting all of these settings  I messed up?

---

### Post by mjhasbach on 2007-04-02
*bump for help*

---

### Post by trent dillman on 2007-04-02
...

---

### Post by justin whitaker on 2007-04-02
> **mjhasbach said:**
> Thats the problem...I only learned about allowing the root to login through GDM after I messed up >_>. How would I go about logging in through the console, and resetting all of these settings  I messed up?

CRTL-ALT-F1 brings up the console. 

If you can login as root (don't know if you can), then you can startx and make whatever changes you need.

---

### Post by mjhasbach on 2007-04-02
Thanks! I slapped a sudo before this "usermod -d /home/username username" and it worked. =]

---

### Post by justin whitaker on 2007-04-02
> **mjhasbach said:**
> Thanks! I slapped a sudo before this "usermod -d /home/username username" and it worked. =]

Fantastic!

---

### Post by Cloudy on 2007-04-02
Please refrain from slapping sudo. :(





(bad jokes abound!)

---

