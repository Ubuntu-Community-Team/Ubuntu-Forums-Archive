---
title: "Changing Ubuntu Login Name"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2008-01-12
I'd like to change my login name for Ubuntu.  What would be the easiest way?

---

### Post by astoltz on 2008-01-12
You can change your login ID using the command "usermod".  The user you are changing can't be logged in at the time so you may have to boot to recovery mode to do this```
usermod --login NEW_USER CURRENT_USER
```NEW_USER should be replaced by whatever you want the new name to be.  Also you should probably change the location of your home directory to match the new name:```
usermod --home -m NEW_USER
```The "-m" will move the files in your current home to the new home.  Leave it out if you want to copy everything.

---

### Post by atraeyu on 2008-01-12
Is it safe to do while logged into the account?  It can safely change all my directories, etc?

---

### Post by astoltz on 2008-01-12
No.  Sorry, I've just editied my first post to reflect that fact.  The user you are changing can't be logged in at the time.

---

### Post by limac on 2008-01-12
i am not that sure about ubuntu, but in kubuntu, you go to the system settings and then click on user management, and from there you can edit your login usrname or pswd. see if there is any similarity in kubuntu and ubuntu, and try to do something like that! :D

---

### Post by atraeyu on 2008-01-12
Yeah, that option is built in.  I didn't know if it was the preferred method or not.  Also - the damn thing requires that the character of the login name be a lowercase letter.  Blah!

---

### Post by limac on 2008-01-12
atraeyu; u figured it out? it is in system > administrator > users and groups! and from there you can edit it! :D

---

### Post by astoltz on 2008-01-12
Damn, limac's solution is way easier.  I just did a test run and the "manage users" application will change a login ID even while that user is logged in.  And it changes the home directory automatically as well.  I'm not sure how it keeps track of everything while you are still logged in as the old user name so personally, I'd still change things while NOT logged in...

---

