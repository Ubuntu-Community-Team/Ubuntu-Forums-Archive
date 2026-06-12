---
title: "[SOLVED] Evolution blocking legit emails"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by MelissaEpiphany on 2007-12-12
Hi,

I just installed Spamassassin in Evolution. Have no idea how to access it to change settings.

For some reason all my emails to my Uni keep getting blocked. All other emails go through but if I try to send to any of my Uni addresses, I get a message back from "M+ Extreme Email Engine" ( my Uni admin address?) that says something along the lines of:

Original messahe recieved from "my addy here."
The following address "Imagine Uni addy here" had a permament error.
The message has been blocked. 
The message has been sent through a system that is blocked by RBL.

Now I might be paranoid, but I did have a bit of an argument with my egocentric full-of-himself  Lecturer, and I really hope it's my system that's blocking those emails and not from his end. 

Can anyone tell me if this message is coming from my email account, why my email account would have spontaneously blocked me from emailing my Uni, and how to correct it?

Cheers Mel

---

### Post by daengbo on 2007-12-13
Can you post a lightly scrubbed header for us? We can probably tell where the block happened.

What is "RBL?" Are you using a local SMTP server or sending mail through a reputable ISP's server?

---

### Post by MelissaEpiphany on 2007-12-14
Hi Daengbo.

Thanks for answering. I'm using SMTP as outgoing. 

From what I understand, RBL is "Realtime Blackhole List" Apparently designed to "assist in the prevention of spam or email abuse." ( Got that from: [http://www.gordano.com/kb.htm?q=264](http://www.gordano.com/kb.htm?q=264). Among other Googled sites.)

Being a month old Noob, I'm not even sure what a "lightly scrubbed header" is ... at risk of looking like an idiot ... ummmmm, what is it? 

The emails that bounce back to me usually say:

From: 	M+ Extreme Email Engine <admin@groupwise.swin.edu.au>
To: 	"My email address is usually here."
Subject: 	Returned mail: Message Blocked
Date: 	Thu, 13 Dec 2007 15:58:34 +1100


The original message was received Thu, 13 Dec 2007 15:58:33 +1100
from "my email address is here."

  ----- The following address had a permanent error -----
    <servicedesk@groupwise.swin.edu.au>; originally to <servicedesk@groupwise.swin.edu.au>
    The message has been blocked.
    ----- the delivery transcript -----
    This message has been relayed through a system that is blocked by RBL

---

### Post by hyper_ch on 2007-12-14
spamassassin does not delete/prevent mails... spamassassin will only TAG emails that it thinks is spam...

Are you trying to operate a mail server from your own computer on dialup/cable/dsl?

---

### Post by daengbo on 2007-12-14
The emails are reaching the destination but being blocked there. It's unlikely that your IT department blocked you specifically so I'm going to guess that you are running your own mail server. If not, whatever SMTP server you route through has been blacklisted.

---

### Post by MelissaEpiphany on 2007-12-16
No I'm not trying to operate a mail server hyper_ch.

Thanks guys. I suspected I was being blocked from that particular address. Interesting ... and seriously disturbing under the circumstances

But Cheers.

---

### Post by discoade on 2007-12-16
you could try signing up to a free pop account online ie lavabit.com or bluebottle.com or the like just to see if they get through! just as a test like!

---

### Post by MelissaEpiphany on 2008-03-13
Thanks to everyone who responded.

After a lot of messing around, and phone calls,  I discovered it had something to do with my service provider. So no my Uni lecturer was not thwarting me perversely, nor was Evolution mail set up or configured wrongly. I went back to getting Uni mail through Uni website and not through Evolution. Evolution is working fine for all other email.

Thanks again to everyone.

Cheers, Mel

---

### Post by dcstar on 2008-03-14
Bogofilter works a lot faster than Spamassassin, and it natively supported by Evolution (you just have to select it in the Preferences).

My Evolution Junk filtering is so much better using Bogofilter I wish I had known about it years ago.

---

