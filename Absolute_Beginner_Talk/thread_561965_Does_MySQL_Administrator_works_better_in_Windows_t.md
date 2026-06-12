---
title: "Does MySQL Administrator works better in Windows than Ubuntu?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-09-28
I am running MySQL Administrator and Query Browser in both Ubuntu 7.04 and Windows (Virtualbox).  

In general I find MySQL  Administrator works more smoothly in Windows than Ubuntu.  Also, when I want to edit table data in Windows, I don't have to enter a password every time I do it.  With Ubuntu I do.  In other word, I see a list of tables, in Windows I don't have to enter a password to edit a table.  In Ubuntu I have to constantly enter a password, every time I move to edit contents of a new table.

I must emphasise, I'm referring to 'Edit Table Data', not 'Edit Table'.

Have I got something wrong?  Is there a way to save the password so I don't have to keep entering it?  

Many thanks - because at the moment, I'm mainly using Windows to use MySQL rather than Ubuntu.

---

### Post by exile on 2007-09-28
I think it has more to do with the login security than the actual management software. I could be that the default windows security has no password by default (I don't know I don't ever use the windows client). I'd check the User Administration section in both to see if they have similar settings.

---

### Post by getmeoutofhere on 2007-09-28
But I have to enter, in Windows as in Ubuntu, the password when I first log into MySQL Administrator.  But in Windows there seems to be a more seemless transition between this and the Query Browser - in a single session, in Windows, I only have to put the password in once, at the beginning.  In Ubuntu, every time I cross from Administrator to Query Browser, I have to enter the password.

---

### Post by OoooMatron on 2007-09-28
The MySQL applications do (unfortunately) run better in windows than linux. (in my experience).

---

### Post by sam_hatoum on 2008-03-12
you can set the password, after you get in, you go to preferences, general options, and choose how to store the password. however, you still get the popup, only now the password is filled.

---

