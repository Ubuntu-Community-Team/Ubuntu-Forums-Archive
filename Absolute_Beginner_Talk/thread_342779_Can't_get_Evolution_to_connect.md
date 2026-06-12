---
title: "Can't get Evolution to connect"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by bradford72 on 2007-01-20
Hello community!
I just threw out windows and installed Ubuntu.  Now that I've got Firefox working correctly, and can access the support forum, I have a question about configuring Evolution.  I get the bulk of my email from gmail, and have enabled POP for my account, written down the config info from gmail, and entered it into Evolution, but cannot seem to get or send mail through Evolution.  At gmail, I am told to connect to the POP server on port 995, and the SMTP server on port 465 or 587.  I haven't been able to figure out how to set these ports for Evolution (and wonder if it is trying to use port 110 for POP...) Any help would be greatly appreciated!

---

### Post by geo_bio on 2007-01-20
> **bradford72 said:**
> Hello community!
I just threw out windows and installed Ubuntu.  Now that I've got Firefox working correctly, and can access the support forum, I have a question about configuring Evolution.  I get the bulk of my email from gmail, and have enabled POP for my account, written down the config info from gmail, and entered it into Evolution, but cannot seem to get or send mail through Evolution.  At gmail, I am told to connect to the POP server on port 995, and the SMTP server on port 465 or 587.  I haven't been able to figure out how to set these ports for Evolution (and wonder if it is trying to use port 110 for POP...) Any help would be greatly appreciated!

Glad you know what you're mostly doing.

the ports 995 and 465 or right. You ALSO need to turn them to SSL security, not TSL or anything else.

I don't use it myself, but I believe that after you set it up, you can go to (maybe) Edit->Account Options, etc...

If you would prefer thunderbird (as I do), you can get thunderbird by going to: Applications->Add/Remove->Internet, and look for thunderbird (I may be wrong as I'm not looking at it right now). If you cant see it, allow commercial and unsupported apps in the Add/Remove window.

---

### Post by bradford72 on 2007-01-20
> **geo_bio said:**
> Glad you know what you're mostly doing.

the ports 995 and 465 or right. You ALSO need to turn them to SSL security, not TSL or anything else.

I don't use it myself, but I believe that after you set it up, you can go to (maybe) Edit->Account Options, etc...

If you would prefer thunderbird (as I do), you can get thunderbird by going to: Applications->Add/Remove->Internet, and look for thunderbird (I may be wrong as I'm not looking at it right now). If you cant see it, allow commercial and unsupported apps in the Add/Remove window.

Thanks for the advise...looking around I discovered that to set ports in Evolution you just need to add the port number to the end of the server address like you would normally do...ie my pop server is pop.gmail.com, so I entered pop.gmail.com:995 and for smtp it was smtp.gmail.com:465....It's still not working, but I thought that little bit of info might be helpful to someone!

Now I can't launch Evolution at all :( I am willing to try thunderbird...but really,the point is just to see what I can make work here, I really don't need either of 'em, but it would be cool to figure out both of 'em...just trying to figure out the whiz-bangs that are included with ubuntu (seems like the best way to learn how to run a new OS is just to play with it...)

---

### Post by bradford72 on 2007-01-20
Well, I got it to work, and I feel like this is kind of "double dipping" but I thought "hey! it works! maybe someone else can use what I got figured out!" So here ya go....Instead of entering smtp.gmail.com:465 in the entry box for outgoing server, I had to use the numbered version 72.14.247.109:465 is the gmail address for smtp server (outgoing) and that made all the difference in the world...the address for the gmail pop server (incoming)  is 66.249.83.111:995 definately DO use SSL encryption for both incoming and outgoing mail. I also selected password authentication for the pop, and login authentication for the smtp

---

### Post by toriam2006 on 2007-06-23
This methold worked for me:

Well, I got it to work, and I feel like this is kind of "double dipping" but I thought "hey! it works! maybe someone else can use what I got figured out!" So here ya go....Instead of entering smtp.gmail.com:465 in the entry box for outgoing server, I had to use the numbered version 72.14.247.109:465 is the gmail address for smtp server (outgoing) and that made all the difference in the world...the address for the gmail pop server (incoming) is 66.249.83.111:995 definately DO use SSL encryption for both incoming and outgoing mail. I also selected password authentication for the pop, and login authentication for the smtp
__________________

---

### Post by monroetransfer on 2008-02-07
Thanks, bradford. Your solution worked for me, too. I CAN SEND MAIL! :)

---

### Post by k1ha on 2008-03-16
Likewise, I cannot get Evolution to send/receive mail.  I am connected via DSL with no problem.  I know not how to get Evolution to respond. It indicates to send but makes no progress.   I know not where to make any settings changes.  I prefer AOL but have not AOL loaded int the system, nor any other windows-based programs (another problem).
Alden

---

