---
title: "evolution email error report"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Bill Ataras on 2008-03-15
With great consistency, my evolution returns an error:

Error while Fetching Mail.
Failed to read a valid greeting from POP server mail.superb.net

I'm not aware of any missing email, or email that failed to get sent, but error messages do concern me.

In response to uname -a, I get:
Linux Decapod 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

and I'm using: evolution 2.12.1.

Not too long ago, my hosting company asked that their customers (at least me!) to make a change to their MX records.  I made what I thought was the correct change at our DNS - zoneedit.com.

Can anyone please help me clear up this problem?

Thanks,
Bill Ataras
:confused:

---

### Post by Mogurijin on 2008-03-15
I'm not a big fan of Evolution. I personally like Thunderbird. There is a slight chance that using Thunderbird would solve this problem, but I'm not sure. It helped when Outlook Express (in Windows) kept failing with my email.

---

### Post by bruce89 on 2008-03-15
> **Mogurijin said:**
> I'm not a big fan of Evolution. I personally like Thunderbird. This is a slight chance that using Thunderbird would solve this problem, but I'm not sure. It helped when Outlook Express (in Windows) kept failing with my email.

Sounds more like a server issue than a software thing, so this would likely yield nothing.

---

### Post by Bill Ataras on 2008-03-15
Thanks for the assistance.  Would an error like this be posted to one of the log files?  If so, can you tell me where to find the file?

Thank you,
Bill Ataras:confused:

---

### Post by dcstar on 2008-03-16
> **Bill Ataras said:**
> With great consistency, my evolution returns an error:

Error while Fetching Mail.
Failed to read a valid greeting from POP server mail.superb.net
..........
Can anyone please help me clear up this problem?


It means exactly what it says, when it tried to contact that mail server it did not respond with a "valid greeting".

It is either and issue with your network connection to that mail server, or that mail server itself.

---

### Post by Bill Ataras on 2008-03-16
> **dcstar said:**
> It means exactly what it says, when it tried to contact that mail server it did not respond with a "valid greeting".

It is either and issue with your network connection to that mail server, or that mail server itself.

Thanks for your response.  I have 6 different email accounts defined in Evolution, and normally all are read at the same time.  To try to figure out which one is at fault, I enabled them, one at a time, and clicked 'send/receive'.  Individually, each of them was read without any failure messages.  Does this give any clues as to what needs to be fixed?

Regards,
Bill Ataras:(

---

### Post by arvana on 2008-04-17
This seems to be a bug in Evolution.  I manage over a dozen email accounts and get this error all the time, with a different domain named in the error each time.  It seems to be an issue with Evolution making multiple connections at the same time -- my workaround was to set the frequency at which Evo checks mail to a different time interval for each account.  This hasn't eliminated the problem, but it reduces the frequency of these errors.

---

### Post by Thaled on 2008-04-21
I also have recently started to receive the  "Failed to read a valid greeting..." message when downloading mail in Evolution. I have 11 email accounts, and have found that as long as I download only 4 at at a time I don't get the error. 

Doesn't matter which 4 that are downloaded, only that the number of accounts downloaded at one time are limited to 4. I love Evolution, having started with outlook Express, then Thunderbird, and now Evolution, but bugs like this sure do bug me. Hope it gets fixed.

---

