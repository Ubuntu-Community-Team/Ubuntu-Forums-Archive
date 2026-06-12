---
title: "cannot login into xwindows(KDE)"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by ashoka2004 on 2006-09-14
hi guys i m facing a new problem


whenever the ubuntu system boots up its gui interface (xwindows) which is the default way by which i login it displays the folowing message


the following installation problem was detected while trying to start KDE no write access to '/home/kapil/.ICEAuthority
kde is unable to start 

then i press ok 
then it displays the following message 

could not start Kmserver check ur installation

then i press ok 
then it brings back to the the login screen then i try for the console login i m able to login

till yesterday after logging in from the console when i was typing startx it was successfully starting the kde but today its displaying the same error message again and again help plz..

---

### Post by jolan_jj on 2006-09-14
I have not much experience with kde, but it looks like you dont have the rights to use ICEauthority file. Try CTRL+ALT+F1, login and ```
sudo chown %yourusername /home/kapil/.ICEAuthority
```

Hope that helps
J.

---

### Post by ashoka2004 on 2006-09-15
hey that helped thanks a ton dude

---

