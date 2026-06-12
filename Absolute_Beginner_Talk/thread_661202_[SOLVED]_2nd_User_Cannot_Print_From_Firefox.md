---
title: "[SOLVED] 2nd User Cannot Print From Firefox"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by hobo on 2008-01-07
I have 2 users defined on my 6.06 image. Problem is that the 2nd user cannot print from Firefox. All it does is spit put a blank page. Printer works fine in her logon otherwise. My logon has no problems whatsoever. Ideas?

---

### Post by kyphi on 2008-01-07
Perhaps you have not given the second user the right permissions.  As boss (superuser) it is up to you to specify what the second user can do.

Go to System -> Administration -> Users and Groups.  Click on the entry for the second user and go to Properties and then to User Privileges.  Place a tick into the appropriate box.

I suggest leaving the 'Executing system administration tasks' unchecked.

---

### Post by hobo on 2008-01-07
Nope that didnt do the trick. I gave her all privleges except exec. Still just spits out a blank page in Firefox. Prints OK otherwise.

---

### Post by kyphi on 2008-01-07
> Still just spits out a blank page in Firefox. Prints OK otherwiseCould you clarify this please.  Do you mean that you cannot print browsed material directly off the internet and that printing a file from your home directory works fine?

---

### Post by hobo on 2008-01-08
> *Do you mean that you cannot print browsed material directly off the internet and that printing a file from your home directory works fine?*

Exactly! Only from Firefox do I have a print problem.

---

### Post by kyphi on 2008-01-09
I am unable to duplicate your problem and cannot find anything to reconfigure.  The version of FF that I have is "1.5.0.13pre" and I have no problem printing from FF.

I sometimes use other browsers besides FF because FF is lacking in some respects.

In Add/Remove you will find Epiphany, Galeon, Kazehakase and Dillo.  I find Galeon particularly useful.

Could you tell me please how you set up the second user?  It seems to me that something went awry there.

---

### Post by hobo on 2008-01-11
Well the 2nd user was able to print from FF but it just quit. FF=1.5.0.13pre also. I am thinking that it has something to do with the FF about:config but it all means nothing to me.

---

### Post by hobo on 2008-01-11
[SIZE="6"]I found the problem ![/SIZE] Somehow she had all her margins set to 5 inches. Do the math.
Thanks for your help.

---

