---
title: "Configuring Pidgin for Gtalk"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-10-21
I installed pidgin 2.2.1 using apt-get install 
i tried configuring it for my gmail account see screenshots 
when i try to connect i get the dialog box shown .
and clicking connect does not do what it is supposed to.
yahoo is'nt working either 
someone help please.

---

### Post by kevdog on 2007-10-21
gmail protocol is jabber I think

---

### Post by cfaulkner on 2007-10-21
Searching google's immense help center:

[http://www.google.com/support/talk/bin/answer.py?answer=24073&topic=1415](http://www.google.com/support/talk/bin/answer.py?answer=24073&topic=1415)

is your answer... :)

---

### Post by chris.m.ball on 2007-10-21
My settings for Pidgin are identical to yours and mine works without issue.  I've been using it for about one week so far to talk to my gf on Google Talk.

---

### Post by wheredidrealitygo on 2007-10-21
Try doing this:

in the modify account section, under the advanced tab, tick the "require ssl/tls" box, the "force old port 5223" box, and manually change the port inside the port field to "5223".

Also the protocol set in pidgin for googletalk is XMPP, not jabber.

That is how mine appears and mine works fine set that way.

---

### Post by techpr on 2007-10-21
Put the Local Alias (any name), maybe it is the problem.

---

### Post by arjayes on 2007-10-22
@ wheredidrealitygo 
i tried that but i'm getting the same dialog but this time showing 
"SSL Handshake Failed"

And i think i used to have the earlier settings  before i had to reinstall ubuntu and they worked fine but that was pidgin 2.1.1 not 2.2.1

---

### Post by alvinistic on 2007-10-22
This is how I get it to work:

Edit your gtalk account
Go to advanced tab
tick the Force old (port 5223) SSL
connect port: 443
connect server: talk.google.com

Try it and Cheers!

---

### Post by arjayes on 2007-10-22
THANKS A LOT .THAT WORKED


But i still can't get my Yahoo messenger working .
i've posted the screenshots of the settings 
sorry to be a pain but i just can't figure it out.

---

### Post by arjayes on 2007-10-22
some one pls reply
:(

---

