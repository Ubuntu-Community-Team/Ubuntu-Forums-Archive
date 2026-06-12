---
title: "User Profiles"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by BeeRad on 2006-10-30
Hi,

   I was wondering why when I switch user and select another user and enter the password the desktop will not load up.  I get a cursor arrow and a brown screen only.  I am trying to set up users for the rest of my family.  I was able to add all the users ok but I can't switch to them.

BeeRad :-?

---

### Post by catlett on 2006-10-30
Adding a user is pretty simple. If you wanted to add me, this is the command 
```
sudo useradd catlett
```
If you wanted to delete me, it would be 
```
sudo userdel catlett
```
The new user will not have sudo powers. To give a new user sudo power, you would have to add them to the sudo file with the vi editor. Vi is hard to use so you can edit with visudo through gedit with 
```
export EDITOR=gedit && sudo visudo
```
When the file opened, you would add me to the sudoers by adding this line to the file
```
catlett  ALL=(ALL) ALL
```
Or you could add me to the admin group and I would get sudo powers without needing to edit visudo.
```
sudo adduser catlett admin
```
Why am I telling you this instead of telling you how to fix the brown screen, because I don't know what is wrong with your users. To start troiubleshooting, I would recommend making a new user with sudo powers using these commands and then seeing if you still get the errors or not.

---

### Post by adam.tropics on 2006-10-31
Not sure how to fix this, but are you able to log into the user accounts from a fresh boot.? ie is it the switching user causing problems or the accounts themselves?

---

### Post by BeeRad on 2006-10-31
Yes, the other users can log in from fresh boot.  I can also login (after) logging out from my profile.  I cannot switch user and login under a different profile.

BeeRad

---

