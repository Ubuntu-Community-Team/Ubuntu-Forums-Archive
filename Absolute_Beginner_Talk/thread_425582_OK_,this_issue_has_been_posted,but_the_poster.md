---
title: "OK ,this issue has been posted,but the poster"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by meman63 on 2007-04-27
I have the same problem that another poster had,but there was no solution to the problem on the previous post.
When I try to login,I get "The system administrator has disabled access to the system temporarily.".
Just like the previous post,I have tried dele user,chmod'ing,etc,to no avail.

PLEASE help me fix this!?
I'M using Feisty.
 Thanks,Monica

---

### Post by meman63 on 2007-04-27
Anyone?
I've been using Fedora Core 6.
I Just came back to Ubuntu,installed Dapper,did an "update-manager" -c to get Edgy.Everything was great(good to be back!).Finished,then decided to try Feisty.
Again,no problem.Installed,and ran,Bastille,trying to make things secure,easily.
Made ny umask=077.Seems the wrong thing to do ,at this point,because now when I reboot I get this "The system administrator has disabled access to the system temporarily."
Afer deleting user,chmoding,.....still no login!
I understand someone else had the same problem,but no fix for users was posted.

Any help?
   Thanks ahead,Monica

---

### Post by meman63 on 2007-04-28
OK,for anyone else that has this problem,here is the solution.Kudos to StarsandStripes14 for the answer.

You will probably have to use recovery console to do this.If you don't know how,simply press Esc on the keyboard after the BIOS screen and choose Recovery mode.Then:
Code :
  cd  /etc/security
Then :  pico access.conf.

Page down to the uncommented line at the bottom(may vary,depending on your setup),usually 
ALL EXCEPT root.LOCAL.Make sure that the symbol before is a +,not a -.That simple.

Like I said,kudos to StarsandStripes14 for this info.

   Enjoy all,
          Monica

---

### Post by JayDeeX on 2007-05-01
Hello,

i just got this issue, and i have no idea how it came to be. the proposed fix about '-' to '+' did fix it, but is this some kind of bug that should be reported?  if not, how did it came to lock me out of my machine?


thanks!

---

### Post by cv_zero on 2007-07-13
ok, the + before that line indicates that only root may login,  ( + all except root )
the - before the line prevents root console login ( - all except root ) 
basically the +/_ controls how the system handles that line of config.
I'm not really sure how you got locked out though...did you change any settings lately, or run bastile?

---

### Post by salehid on 2007-07-18
I think I have the same problem ....

---

