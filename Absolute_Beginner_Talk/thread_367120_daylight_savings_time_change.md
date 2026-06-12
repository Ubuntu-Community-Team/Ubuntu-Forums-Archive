---
title: "daylight savings time change"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-02-21
Can anyone tell me if Ubuntu has anything in place or in the works to compensate for the soon to come change in when daylight savings time begins and ends ?

I have searched in this forum and so far I see nothing or very little regarding this issue.

Thanks.

---

### Post by linux_kid on 2007-02-21
> try this:
Quote:
xxx@xxx:~$ sudo zdump -v /etc/localtime |grep 2007
/etc/localtime Sun Mar 11 07:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime Sun Mar 11 08:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime Sun Nov 4 06:59:59 2007 UTC = Sun Nov 4 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime Sun Nov 4 07:00:00 2007 UTC = Sun Nov 4 01:00:00 2007 CST isdst=0 gmtoff=-21600
if you have results similar to above you should be okay. if not you may have a non-standard setup and will have to update your tzdata manually. or update to the latest libc6 package.

most recent distro's are okay.

Your results should be exactly the same.  The update was in an update package.

---

### Post by wpshooter on 2007-02-21
Am I correct in that if I see March 11th and Nov. 4th, then I am good to go, even though the times in my printout vary from your ?

Thanks.

---

### Post by yabbadabbadont on 2007-02-21
> **wpshooter said:**
> Am I correct in that if I see March 11th and Nov. 4th, then I am good to go, even though the times in my printout vary from your ?

Thanks.

You should be.  Your output would only be the same as his (and mine by the way) if you are in the US/Central timezone.  As long as the dates are the same, then you should be good.

---

### Post by linux_kid on 2007-02-21
EDIT: Above post explains it.

---

### Post by wpshooter on 2007-02-21
Thanks to both of you for the help.

---

### Post by linux_kid on 2007-02-21
Your Welcome :popcorn:

---

### Post by yabbadabbadont on 2007-02-21
> **linux_kid said:**
> Your Welcome :popcorn:

Since I seem to be the one to translate linux_kid's posts...  What he means is, "You're Welcome."  :D :lol:

I'm glad I could help too.  ;)

---

### Post by linux_kid on 2007-02-21
> Since I seem to be the one to translate linux_kid's posts... What he means is, "You're Welcome."

Almost Every time I post here, I have a translator. :guitar:

---

### Post by yabbadabbadont on 2007-02-21
> **linux_kid said:**
> Almost Every time I post here, I have a translator. :guitar:

While I (usually) need someone to be my spell checker...

:lol:

---

### Post by Ramses de Norre on 2007-02-28
Welcome to Firefox 2 with his build in spell checker ;)

---

### Post by Buddha443556 on 2007-02-28
> zdump -v /etc/localtime |grep 2007
That command should work fine without SUDO, worked for me.

---

### Post by yabbadabbadont on 2007-02-28
> **Ramses de Norre said:**
> Welcome to Firefox 2 with his build in spell checker ;)

Yes, but it doesn't correct it when you use the wrong word (that happens to be spelled correctly).  :lol:

P.S.  "build in" is not correct.  It should be, "built in".  ;)

---

### Post by steven8 on 2007-02-28
My system is good to go!

---

### Post by Sunflower1970 on 2007-03-01
Woohoo! I'm good to go too! :)

---

### Post by Ramses de Norre on 2007-03-02
> **yabbadabbadont said:**
> Yes, but it doesn't correct it when you use the wrong word (that happens to be spelled correctly).  :lol:

P.S.  "build in" is not correct.  It should be, "built in".  ;)

I hate those "build vs built" stuff... Well, another example of the imperfectness of spell checkers.

---

### Post by Arndt on 2007-03-02
> **Ramses de Norre said:**
> I hate those "build vs built" stuff... Well, another example of the imperfectness of spell checkers.

Since we're picking nits, it's "daylight saving time", not "daylight savings time".

---

### Post by dwblas on 2007-03-02
> What he means is, "You're Welcome."No, he actually stole your welcome and was saying that he was using it instead of his own.

---

### Post by yabbadabbadont on 2007-03-02
> **dwblas said:**
> No, he actually stole your welcome and was saying that he was using it instead of his own.

Well technically, it was his welcome to begin with.  He posted the commands to verify compliance.  ;)

---

### Post by dwblas on 2007-03-03
> Since we're picking nits, it's "daylight saving time", not "daylight savings time".Since we are still nit picking, which is a good thing every once in a while, no daylight is saved.  We should be using a more descriptive (and honest) term like "summertime" even though it lasts a good deal longer than that.  "Daylight saving time" is evidently a term used by politicians to put a good spin on it so they could sell it in the first place.  Thinking that someone will believe that daylight is saved is just calling them stupid.

---

### Post by thepaul on 2007-03-03
I ran the command and this is what I get:


/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000


I presume I have some problem.  What do I need to do to fix it?

---

### Post by dwblas on 2007-03-03
You have Sunday, March 11, and Sunday November 4.  That's what the previous post said it should be.

---

### Post by thepaul on 2007-03-03
I see

I thought the other numbers were the ones that determined whether it was going to work.


Thank you for pointing that out.


take care

---

### Post by kcallis on 2007-03-12
> **linux_kid said:**
> Your results should be exactly the same.  The update was in an update package.

I have the latest upgrades, but my time is still not updated correctly! How do I make the change correctly?

---

### Post by iguanamind on 2007-03-12
I also have the correct output from that zdump but my clock was not set properly for DST.  Not sure what the problem is.

---

### Post by rlsteelman on 2007-03-14
I have this one:

> 
/etc/localtime  Sun Apr  1 07:59:59 2007 UTC = Sun Apr  1 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Apr  1 08:00:00 2007 UTC = Sun Apr  1 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Oct 28 06:59:59 2007 UTC = Sun Oct 28 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Oct 28 07:00:00 2007 UTC = Sun Oct 28 01:00:00 2007 CST isdst=0 gmtoff=-21600


Needless to say my damn time isn't up to date.:(

---

### Post by oilchangeguy on 2007-03-14
i found this real simple. right click on the clock, adjust time, check the box to update from the internet time servers, select a few servers and your done. no need to get all wraped up in command lines.

---

### Post by kcallis on 2007-03-15
/etc/localtime  Sun Apr  1 09:59:59 2007 UTC = Sun Apr  1 01:59:59 2007 PST isdst=0 gmtoff=-28800
/etc/localtime  Sun Apr  1 10:00:00 2007 UTC = Sun Apr  1 03:00:00 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Oct 28 08:59:59 2007 UTC = Sun Oct 28 01:59:59 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Oct 28 09:00:00 2007 UTC = Sun Oct 28 01:00:00 2007 PST isdst=0 gmtoff=-28800

I have deleted /etc/localtime and allowed ntpd to retrieve the correct date. My current libc6 is 2.4-1ubuntu12.3. I guess I need to go and see if there is recent localtime to replace what is coming down the pipe.

**EDIT:** To finally get things working correctly, I had to do the following:

#zdump -v /etc/localtime | grep 2007

to verify the 2007 timezone settings. Mine showed April 1st as the date of change... and not March 11.

I went to [http://www.twinsun.com/tz/tz-link.htm](http://www.twinsun.com/tz/tz-link.htm) and downloaded tzdata2006p.tar.gz. I un-tared this file into a temp directory and executed

# zic -d /tmp/zoneinfo northamerica

to compile the timezone data files. I then copied the EST5EDT file to /usr/share/zoneinfo/ directory and America/Montreal file into /usr/share/zoneinfo/America directory. Doing a quick test will make sure these new files are good.

# zdump -v /usr/share/zoneinfo/EST5EDT | grep 2007
# zdump -v /usr/share/zoneinfo/America/Montreal | grep 2007

lastly I linked the localtime file

# ln -fs /etc/localtime /usr/share/zoninfo/PST
# zdump -v /etc/localtime | grep 2007

the expected output should look a little like this

/etc/localtime Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime Sun Nov 4 05:59:59 2007 UTC = Sun Nov 4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime Sun Nov 4 06:00:00 2007 UTC = Sun Nov 4 01:00:00 2007 EST isdst=0 gmtoff=-18000

Hope this helped.

---

### Post by lisati on 2007-09-21
> **yabbadabbadont said:**
> While I (usually) need someone to be my spell checker...

:lol:

"Your" and "you're" catches a lot of people I know out, some of whom have Enslish as a second language.

---

### Post by yabbadabbadont on 2007-09-21
Holy thread resurrection Batman!
> **lisati said:**
> "Your" and "you're" catches a lot of people I know out, some of whom have Enslish as a second language.

Including you it would seem.  :D   "Enslish->English"  (or are you, like me, just a bad speller?  ;))

---

### Post by nlvivar on 2007-11-10
You can try <code>sudo dpkg-reconfigure tzdata</code> first in a terminal. That should give you a walk-through to choose your timezone and check if that corrects.

If that still doesn't work, you should make sure that you have the correct ubuntu repositories up for apt, and reinstall tzdata. I had a 2007 package reinstalled for my Gutsy installation.

-Noel

---

### Post by Footer on 2007-11-13
I have an interesting problem in this regard.  My time shows correctly on my desktop and at the command prompt:

```
footer@kubuntu64:~$ date
Tue Nov 13 07:20:12 CST 2007

```

zdump looks correct too:

```
footer@kubuntu64:~$ sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 07:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Mar 11 08:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  4 06:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  4 07:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 CST isdst=0 gmtoff=-21600

```

Yet the time in my log files still shows daylight saving time (one hour later) as do file times when I modify them:

```
footer@kubuntu64:/var/log$ tail -f syslog
Nov 13 07:36:17 kubuntu64 syslogd 1.4.1#21ubuntu3: restart.
Nov 13 07:36:17 kubuntu64 anacron[14272]: Job `cron.daily' terminated
Nov 13 07:36:17 kubuntu64 anacron[14272]: Normal exit (1 job run)
Nov 13 07:46:44 kubuntu64 -- MARK --
Nov 13 08:06:45 kubuntu64 -- MARK --
Nov 13 08:17:01 kubuntu64 /USR/SBIN/CRON[23785]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

I've tried everything in this thread except post #28 (which I'll try when I have time).  Looking for suggestions if anyone else has experienced this weirdness and fixed it.

Thanks!

---

