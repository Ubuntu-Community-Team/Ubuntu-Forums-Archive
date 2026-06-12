---
title: "Nawk question"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by bajetownrep on 2006-12-10
Hello all I am receiving an error when attemting to use nawk

I want to pipe the output from the date command and extract the month and year fields and place them on two different lines

So the output should be 

Month: Dec
Year:2006

I run this from the command line

date|nawk '{print "Month:"$2"\n Year:$6}'

However I receive a runaway string constant error.


Can anyone shed light on what I am doing wrong

---

### Post by David_T on 2006-12-10
Sure - you are missing a quote.  You probably want:

date|nawk '{print "Month:"$2"\nYear:"$6}'

---

### Post by bajetownrep on 2006-12-10
awesome that worked 

thanks a lot man.

just to solidify the quoting and newline concept. say I wanted day on a new line after year would it be the following 

date|nawk '{print "Month:"$2"\nYear:"$6"\nDay:"$1}

thanks again for the help. The use of the newline was puzzling me there for a second and the nawk man page is a bit terse to say the least

I also wonder if you could clarify an error I received in a tcsh script i was trying.

---

### Post by David_T on 2006-12-10
Cool :)
And just as an aside, you don't need awk for this:

date +Month:%t%B%nYear:%t%Y

---

