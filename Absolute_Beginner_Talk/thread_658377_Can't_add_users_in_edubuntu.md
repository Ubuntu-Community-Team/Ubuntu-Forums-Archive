---
title: "Can't add users in edubuntu"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by iceman0304 on 2008-01-04
I can't seem to add users to edubuntu.  I installed the software and updated software.  Now when I login in with the name I gave it, I have to enter it twice to start it up..

  I click <System> <administration> <users and groups>    It brings up USERS SETTINGS (panel) it shows 2  the name I gave it during install    (name) and (root)     I didn't have to type in a password or anything (maybe this is normal, plus I'm assuming I'm the administrator with my normal login)   the only way I get the ADD USER button to activate is by clicking the UNLOCK button at the bottom near the CLOSE button.

I click the ADD USER button, NEW USER ACCOUNT panel opens, I enter USERNAME, USER PASSWORD add or check Privileges or even leave it alone just to try to get anything.  Click the OK button and everything (Users Settings panel & New user account panel) closes.

Open up Users and Groups again nothing has changed

do I have to login as root? if so how? I don't remember ever entering a password for it, I only used the name that I installed it with and the password for it allows me access everything with it, it seems..

Any ideas please..   I have alittle experience with linux

---

### Post by kestrel1 on 2008-01-04
It may be because you are not using a password. Go to the users panel again & set a password for yourself. Logout & login with your new password & try again,

---

### Post by iceman0304 on 2008-01-04
I have to login to get to the desktop, I login with a name, the one that was given during install (assuming this is the administrator) this is not root I have no idea what the root password is I try to change it when I'm in the Users and Groups panel but no changes are excepted everytime I click the OK the panels all close.

---

### Post by kestrel1 on 2008-01-04
Try adding the user through the terminal:
```
sudo adduser benny
```
where 'benny' = your users name.
This should create the user then ask you for the password, name etc.

---

### Post by iceman0304 on 2008-01-04
Ok that did add a user, now is this a superuser? It shows no privileges.

---

### Post by kestrel1 on 2008-01-05
If you go back to the Users and Groups GUI, you should be able to set the privilages to how you want.

---

