---
title: "prstat output"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-05-28
i want to capture the *prstat* output to a file. since it is dynamic it is not quitting and hence i feel difficult to capture it. i want in the form of shell script. pls tell me how to do that.

---

### Post by freebird54 on 2007-05-28
if you add

> filename

to end of your call, it should redirect to a file just fine.  I think it sets the ntop and nbottom to 15 and 5 by default in that case.  You might want the -c option as well - for not overprinting - haven't tried it :)

Sorry - haven't done much scripting recently (since 88 perhaps!?) so can't do that for you quickly!

---

### Post by sankarv on 2007-05-28
if iam redirecting it to a file it is not quitting/ ending the call to prstat. that is the problem. i just want a snapshot of prstat 1 time static output to a file thats enough. no need for the dynamic changes going on.

---

### Post by freebird54 on 2007-05-28
Just start it with **count == 1** as an option.  It defaults to continuous, but allows a count option.  Tell you what - here is a man page (if you don't have one handy):

[http://www.scit.wlv.ac.uk/cgi-bin/mansec?1M+prstat](http://www.scit.wlv.ac.uk/cgi-bin/mansec?1M+prstat)

that ought to do it for you.  Set count to 1, and redirect to file.  Or set count to *n*, use -c, and redirect to file.  Should do you!

Enjoy...

---

### Post by sankarv on 2007-05-28
thats great. it works fine.


it is ok with

> *prstat  -Lc  5 2*

command which specifies the interval as 5 seconds and count as 2 so that it evaluates twice  in 5 seconds and i can redirect that to a file.


Thanks for the help...

---

### Post by freebird54 on 2007-05-28
Glad you got it!  You wouldn't want the whole hard drive filled up with a runaway - so I guess it made sense to put a count in there, right?  Hope it tells you what you want to know...

---

