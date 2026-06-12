---
title: "change usernae"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-05-09
how do i delete the user name i am useing now to login with, and add a new user name instead of the one i am useing?


lex1:)

---

### Post by ncappel1 on 2006-05-09
to do it in the gui you can go into System-->administration-->users and groups, then do all the work from in there. in the terminal the command is
```
sudo adduser <new user name>,
<users new password>
```

edit: for more info:
[https://wiki.ubuntu.com/AddUsersHowto?highlight=%28adduser%29](https://wiki.ubuntu.com/AddUsersHowto?highlight=%28adduser%29)

---

### Post by lex1 on 2006-05-09
thanks for post but how to delete present user name?

lex1

---

### Post by jasay on 2006-05-09
Ok, I haven't done this, but it sounds logical to me.  Someone please point out any potential problems.

First, if the old user was the admin (aka could use sudo) make sure the new user (or at least some other user) is allowed to perform administrative duties.  That is: open system > administration > user and groups, then double-click the user you want to make the new admin, go to the user privileges tab, and check "executing system administrative tasks."

Click ok.  Close the program.  Log out, log in as the new user.  Go back to the user and groups program and delete the old user. 

Deleting users doesn't seem to delete their home directory so (after backing up anything important of course!) you might follow the whole thing up with a ```
sudo rm -r /home/username
```

---

