---
title: "password for www-data"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by tedk on 2007-07-18
I installed apache from the Synaptic Package Manager. It's running fine. I noticed that it runs as user www-data and that this user has a password. I never set a password for www-data. What happens if I remove or change the password it has.I, of course, can't see what it is ... it just reads *** in "Users and Groups."

I know that I can edit /etc/sudoers and then sudo as www-data. But my question is not so much operational as policy. www-data has a password. I did not assign it. But it must be used for something. I cannot use it becasue I don't know what it is. If I cange it to something that I know, will I break whatever might be using the one I don't know?
 -ted

---

### Post by X-626 on 2007-07-18
www-data doesn't really have a password.  Its password entry in /etc/shadow is just an asterisk (*) which means that there is no possible character combination that can equal that.  I'm not sure about changing the password, though.  Usually, for daemons (programs that run in the background), they don't have a password.  It's for security purposes, I think.

---

### Post by tedk on 2007-07-18
Thanks ... I hadn't thought about looking at shadow. What I did was look at System->Users and Groups, selected www-data and clicked on Properties. A series of splats is shown as the password in the same way it shows for my user account. But I do see the spats for all the system users.

 -ted

---

