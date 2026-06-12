---
title: "trouble with group permissions"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by dixonstalbert on 2007-06-19
hello

I am having trouble setting up group permissions with the Administation applet Users and Groups.

Here is what I did:

I. I created a new user account 'John' and set a password.

2. I created a new group account 'test' and added my user account 'Dixon' and 'John' to it.

3. I logged in to 'John' account and set /home/John permissions to user=John group=test and gave group full privileges

4. I logged into 'Dixon' user account and tried to access /home/John and got 'permission denied' message-even though Dixon is in group and group has read write execute privileges

I redid the same steps using terminal commands but did noit have any better luck.

what i am trying to do is create another user account that could access pictures in my home directory but not business files subdirectory. is there an easy way to do this?

I am going to try the old MSwindows trick of rebooting to see if problem magically fixes itself.

Thanks in advance for any help :popcorn:

dixon

---

### Post by dixonstalbert on 2007-06-19
yep, works fine since rebooting.

good old on/off switch on front of computer fixes another one...

---

