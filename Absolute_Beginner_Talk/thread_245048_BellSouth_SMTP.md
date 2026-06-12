---
title: "BellSouth SMTP"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by clyjohns on 2006-08-27
Just installed Ubuntu yesterday and love it so far!:)  I do have a problem I hope someone can help me with.  Has anyone had any experience in setting up Evolution or Thunderbird with BellSouth.net's email service?
I can receive fine on POP, but when I try to send a message I get this error:
RCPT TO <unsername@whatever.net> failed: Requested action not taken: mailbox unavailable

BellSouth uses mail.bellsouth.net as both POP and SMTP servers and from my understanding I will have to use SMTP_AUTH as a client to their server and PLAIN for authentication.  I tried that in setting up the account on Evolution and still get the error.  BellSouth is just not very friendly to the Linux community.  If anyone can offer any assistance, I'd sure appreciate it.

---

### Post by BDG on 2006-08-27
Evolution + Bellsouth.net = no prob. here (sending or receiving)

---- BellSouth uses mail.bellsouth.net as both POP and SMTP servers ----

Should be      mail.clt.bellsouth.net

---

### Post by clyjohns on 2006-08-27
Tried mail.clt.bellsouth.net   wont work either.
I have edited the /etc/postfix/main.cf file to include bellsouth in the relayhost  that didnt work either.
Can someone who has Bellsouth set up with Evolution tell me how they did it?

---

### Post by LordKthulhu on 2007-08-24
clyjones - offtopic, but wonder if you (or anyone else who reads this) might know. I am on BellSouth DSL using their Westall 6100 modem (not connected yet). What drivers (if any) do I need to run this sucker? My computer (running Feisty) doesn't seem to even see the thing. Thanks!

---

### Post by caro on 2007-08-24
> **clyjohns said:**
> Tried mail.clt.bellsouth.net   wont work either.
I have edited the /etc/postfix/main.cf file to include bellsouth in the relayhost  that didnt work either.
Can someone who has Bellsouth set up with Evolution tell me how they did it?

I have a BellSouth account set up and working in both Evolution and Thunderbird.  No editing done to /etc/postfix/main.cf needed on my machine.  Here are the settings:

You can use mail.bellsouth.net as the mail server for both incoming and outgoing mail. 

For incoming mail, use Password authentication.  For outgoing mail, use Login authentication and the server does require authentication.  No encruyption.  

Your username should not include "@bellsouth.net"

Hope this helps.

---

### Post by caro on 2007-08-24
> **LordKthulhu said:**
> clyjones - offtopic, but wonder if you (or anyone else who reads this) might know. I am on BellSouth DSL using their Westall 6100 modem (not connected yet). What drivers (if any) do I need to run this sucker? My computer (running Feisty) doesn't seem to even see the thing. Thanks!

Well, I set up my DSL a while ago when I was still using Windows and I have a Linksys wireless router that my Ubuntu laptop connects to, so I don't have any answers here for you unless you are also using a router.  If so  and you have questions about settings, post or PM me.

---

