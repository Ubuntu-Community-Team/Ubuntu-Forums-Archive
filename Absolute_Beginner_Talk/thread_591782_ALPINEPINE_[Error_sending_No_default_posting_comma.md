---
title: "ALPINE/PINE: [Error sending: No default posting command.]"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-25
As you probably gathered from the title, I"m using alpine/pine to send mail for the first time, and when I do, I get this message and it doesn't send the message:
> 
[Error sending: No default posting command.]


any ideas?

---

### Post by Hospadar on 2007-10-25
I'm not all to familiar with pine, but I might suspect that maybe your outgoing mail server is not configured properly?

---

### Post by ryanVickers on 2007-10-25
how would I reconfigure it then?

---

### Post by ryanVickers on 2007-10-26
OK, I changes (I don't remember what) to be smtp.gmail.com or something, and now it actually get's to this thing that says "[sending mail |    0%    |]" and then it takes a really long time and does this "[Error sending: Connection failed to gmail-smtp.l.google.com,25: Connection timed out]"

it shouldn't take that long! the message was "test message - EOF"! ](*,)

---

### Post by jdarias on 2007-11-07
I am in the search to configure alpine for gmail too. I don´t have a clue about it, but my instinct tells me you may have a problem with the ssl/tls thing gmail requires.
Btw if you´re sucessful getting it to work, come back and share the howto! :)

---

### Post by malaprohibita on 2007-12-09
any updates on getting alpine to successfully connect to gmail?

---

### Post by ryanVickers on 2007-12-09
doesn't look like it's going to work... I guess it doesn't matter too much, but it would have been nice :p

---

### Post by stefaneb on 2007-12-11
I had a similar error here at work, solved by editing .pinerc as suggested:

Sendmail-Path=/usr/lib/sendmail -oem -t -oi

This was not originally set, but the comments in the rc file indicated it was a good idea.  It worked for me, not sure about with gmail though.

---

### Post by malaprohibita on 2007-12-12
I had some luck following the link below:
[http://jayson-r.livejournal.com/2151.html]("http://jayson-r.livejournal.com/2151.html")

There were some issues with the SSL certificate, but once I told alpine it was okay it seems to work just fine.

---

