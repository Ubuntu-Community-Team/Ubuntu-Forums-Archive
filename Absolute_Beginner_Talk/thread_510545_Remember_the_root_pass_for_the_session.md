---
title: "Remember the root pass for the session"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-07-26
How can I make Ubuntu remember my password for a session? I don't want to enter passwords again and again after the first time entry in the login screen.

This was a feature in Debian and since Ubuntu is a derivative of it I am almost certain that there was a program that let you do that.. But I can't remember the name.

So what was it? Or do you know of another way?

---

### Post by skymera on 2007-07-26
i cant see why you would want to stop it

[www.ubuntuguide.org](www.ubuntuguide.org)

i think theres a section on this :)

---

### Post by Majorix on 2007-07-27
It can't be that insecure if other named distros implement it, or can it?

So is there any way?

---

### Post by Majorix on 2007-08-04
Anyone?

---

### Post by ugm6hr on 2007-08-04
Have a look at this:
[http://ubuntuforums.org/showpost.php?p=765603&postcount=4](http://ubuntuforums.org/showpost.php?p=765603&postcount=4)

From *man sudoers* (for full explanation):
>        timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for
                   a passwd again.  The default is 15.  Set this to 0 to
                   always prompt for a password.  If set to a value less than
                   0 the user’s timestamp will never expire.  This can be used
                   to allow users to create or delete their own timestamps via
                   sudo -v and sudo -k respectively.


So I believe that setting the timeout to -1 would keep it alive for the entire session.

Personally I agree with various other comments - there is a good reason for having a timeout.

---

### Post by Majorix on 2007-08-04
Ok I did that.

Though I did it using sudo tee -a to append at the end of file. I guess this caused this error I am getting now when trying to save the file:

> Could not save the file /etc/sudoers.
You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.

Can anybody help with this issue?

I know I should have just sticked with editing it manually but what is done is done. Can't change.

Thanks a lot.

---

### Post by Majorix on 2007-08-04
And worse is it didn't work :(

---

