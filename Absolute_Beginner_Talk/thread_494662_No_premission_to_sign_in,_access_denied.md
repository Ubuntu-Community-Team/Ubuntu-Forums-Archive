---
title: "No premission to sign in, access denied?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ETS_5005 on 2007-07-07
Did something what I should not have been done ](*,). Anyway when i sigh in a note that files of my user are been ignored...further on the note of being logged in for less than 10 sec appears. The error note had something in the type of that Access denied to /my user name/home/. Will go back and try to recover some more details.

---

### Post by ETS_5005 on 2007-07-07
[IMG]http://img255.imageshack.us/img255/1182/error1yx6.th.jpg[/IMG]                    [IMG]http://img176.imageshack.us/img176/852/erroooor2yf4.th.jpg[/IMG]
[http://img255.imageshack.us/img255/1182/error1yx6.jpg](http://img255.imageshack.us/img255/1182/error1yx6.jpg)     [http://img176.imageshack.us/img176/852/erroooor2yf4.jpg](http://img176.imageshack.us/img176/852/erroooor2yf4.jpg)

---

### Post by steve.horsley on 2007-07-07
I can't read those thumbnails. 

Does it drop you back to a black screen with white text? If so, pressing enter should get you a login prompt. What happens if you try and log in there?

---

### Post by ETS_5005 on 2007-07-07
Sorry about that. It throws me back to login prompt and from there on the cycle repeats. I log in. Same error notes. :(

---

### Post by ETS_5005 on 2007-07-07
Once again found something useful 

[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

Will try.

Nothing 
chmod:missing operand after '644/home/user/.dmrc

---

### Post by steve.horsley on 2007-07-07
There should be a space between 644 and /home/user/.dmrc.
While trying to fix that problem, this command might also help:
**sudo chown user:user /home/user/.dmrc**

In all the above commands, replace "user" with your username.

---

### Post by ETS_5005 on 2007-07-09
No worry. Re-installed Ubuntu. Did not had the time to search. And had not the will. So i went the easier way. Thank you anyway.

---

