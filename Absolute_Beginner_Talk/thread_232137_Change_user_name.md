---
title: "Change user name"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by gn2 on 2006-08-08
Apologies in advance if this has been covered before/elsewhere, but I can't find it.....

My problem is that when I installed Ubuntu I was asked for a user name. I chose to call myself "user" which I thought was a smart move, because I wouldn't forget it.....

Now when I send mail using Evolution the receiver sees it as being from "user" and deletes it, believing it to be dodgy...

Not feeling so smart now.....

How do I change the super-user name?

---

### Post by Paerez on 2006-08-08
The super-user is called "root". Your account, named "user" is just a regular user.

OK, now on to a solution:
[http://howtos.linux.com/guides/sag/x2424.shtml](http://howtos.linux.com/guides/sag/x2424.shtml)

That tells you how to change the user name. Then this shows you how to give them a new home:
[http://www.ahinc.com/linux101/users.htm](http://www.ahinc.com/linux101/users.htm)

Then you can use the command:
```
mv /home/old /home/new
```

Make sure to back-up your data first! Just in case!

---

### Post by gn2 on 2006-08-08
Thanks for quick post, had a look at suggestions but looked a bit complex for a noob like me...

Have solved the mail problem by creating a new user for myself.
That has fixed the sender appearing wrongly.

In Windows I never bothered with User Accounts, they were more hassle than I could be bothered with...

However it seems easier in Ubuntu.

---

### Post by Paerez on 2006-08-08
Yeah the best way would be to just create a new user, log in as that user, and copy everything from the old user's home to the new user's home.

If you copy all the files and folders that start with a "." in your old home, that will import your settings.

---

