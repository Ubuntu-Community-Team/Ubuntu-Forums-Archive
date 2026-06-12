---
title: "Remove myself from admin group - can't sudo anymore!"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by gertoft on 2006-07-24
Hi.

I created a new group called web to have as group owner for all my web files. I then added myself to that group with the command
sudo usermod -G web "my_user"

After that I can't sudo anymore! :( 

My guess is that I by the usermod command removed myself from the admin group that I should be a member of to be allowed to do sudo and su -. ](*,) 

What can I do to get the sudo rights back?

//Nick

---

### Post by philippe_carlo on 2006-07-24
Boot in recovery mode and add yourself back to the admin group.

---

### Post by aysiu on 2006-07-24
> **philippe_carlo said:**
> Boot in recovery mode and add yourself back to the admin group.
Here's how:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by gertoft on 2006-07-24
Thank you very much guys, you've saved my vacation! :D 

//Nick

---

