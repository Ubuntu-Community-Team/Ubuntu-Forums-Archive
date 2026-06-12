---
title: "Crontab - Run every 20 min?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by iluminate on 2007-02-12
Hi all,

I think I have misunderstood the way time is handled in crontab. What  I do not understand is how do I make a script run every 10 min, or every 15 min or every 20 min?

I tried with 0,10 * * * * and 0,15 * * * *  << Is this correct?

When I check the logs it seems that the script is executed every hour and 10 min past, but not each 10 min (or 15).
Can someone solve this or do I have to call Sherlock? :) 

Cheers

---

### Post by kaptainlange on 2007-02-12
> **iluminate said:**
> Hi all,

I think I have misunderstood the way time is handled in crontab. What  I do not understand is how do I make a script run every 10 min, or every 15 min or every 20 min?

I tried with 0,10 * * * * and 0,15 * * * *  << Is this correct?

When I check the logs it seems that the script is executed every hour and 10 min past, but not each 10 min (or 15).
Can someone solve this or do I have to call Sherlock? :) 

Cheers

If I understand, you want to execute a command every 10 minutes/15 minutes?

then it should just be:

```
X * * * *
```

Where X is the time in minutes you want to wait

**Edit**
**This information is incorrect for this problem**

---

### Post by compmodder26 on 2007-02-12
For every 10 minutes you would need an entry like this

0,10,20,30,40,50 * * * * <command>

Just adjust the intervals for 15, 20, etc.

---

### Post by compmodder26 on 2007-02-12
> **kaptainlange said:**
> If I understand, you want to execute a command every 10 minutes/15 minutes?

then it should just be:

```
X * * * *
```

Where X is the time in minutes you want to wait

No, that would only run the command at minute X of every hour.  The OP needs to provide a comma separated list of every minute he/she wants to the command to run.

---

### Post by kaptainlange on 2007-02-12
Ah Ha, I see what you mean.  Thank you for correcting that.

---

### Post by kittyhawk63 on 2007-02-12
I've not been able to post here. I've been only able to post to the other tags. How did you do it.
kittyhaw63

---

### Post by Bachstelze on 2007-02-12
Instead of 0,10,20,...,50, you can put */10, which will run the command when the number of minutes in the hour is dividable by 10, i.e. every 10 minutes.

---

### Post by compmodder26 on 2007-02-12
I had never seen that syntax before and it isn't listed in the man pages I've looked at.  But I tried it out and crontab seems to accept it as valid syntax.

---

### Post by iluminate on 2007-02-12
> **HymnToLife said:**
> Instead of 0,10,20,...,50, you can put */10, which will run the command when the number of minutes in the hour is dividable by 10, i.e. every 10 minutes.

Hmm or maybe */6 = every 10 min?  Or as you wrote it ?
Meaning that this */10 has to be in hours and not minutes? Like this -
* */10 * * *
or
*/10 * * * * ?

Maybe its possible to do 0/10 * * * * which will run every 10 min also?

I do not know but until I get this with crontab it will remain very cryptic =)

---

### Post by santosgtac on 2008-03-26
There are 5 fields and * indicates any. If
field          allowed values
 -----          --------------
minute         0-59
hour           0-23
day of month   1-31
month          1-12 
day of week    0-7

"how do I make a script run every 10 min, or every 15 min or every 20 min?" This is acomplished with the use of the / followed by a number and the field. This is the value of the first blank in run every __  __, and the field above answers the second blank. 

So if I want to run a script every _10_ _minutes_. The crontab would start with a the range (see above). In minutes this is 0-59. 

0-59/10 * * * *

Run every 20 minutes:
0-59/20 * * * *

Run every 2 hours on the hour:
0 0-23/2 * * *

You get the idea.

---

