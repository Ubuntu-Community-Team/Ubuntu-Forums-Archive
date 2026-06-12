---
title: "Cannot log in"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Jem00 on 2007-10-08
Hey guys,

I just installed Ubuntu 7.04 on a toshiba satellite a30 laptop.
Now everytime I try to log in with the user id I created in the instllation it hangs....so i have to do a BACKSPACE+CTRL+ALT.

So what I did was went into recovery mode and created a new user....no administrative rights because i'm not sure how to do that.....and I can log in and use ubuntu with this user.

How would I go about fixing the other user?
Or is there a better way of doing things?


Thanks for your help guys..

---

### Post by bobplano on 2007-10-08
you could have added them to the admin group when you made the user so 
```
sudo adduser *username* admin admn
```

i don't know if you still need to be in the admn group or not

you could rsync over all your files then delete the original user and home folder. but i hope there is a better way to fix it

---

### Post by Jem00 on 2007-10-08
OK so say I delete the current user I made and create a new one with administrative privileges....how can I delete the first user I created

---

### Post by bobplano on 2007-10-08
use recovery mode again.

---

### Post by Jem00 on 2007-10-09
Hey..wat is the code for deleting a user though recovery mode?????????

---

### Post by macogw on 2007-10-09
Just make the new admin user in recovery mode then use that user in System > Admin > Users & Groups to get rid of the old one.  I think it's "deluser" though.

---

### Post by Jem00 on 2007-10-09
Thanks for all your help guys... I already figured it out....

Just for all those people who have the same problem i write out what i did

Firstly I went into recovery mode created a new user and added him to the admin group.

Thanks for your help anyway

---

