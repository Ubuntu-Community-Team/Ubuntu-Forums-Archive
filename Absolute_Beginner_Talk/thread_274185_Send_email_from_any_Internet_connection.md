---
title: "Send email from any Internet connection?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by phalon on 2006-10-09
I am running Dapper 6.06 (standard, out of the box, no special apps or packages)(and I love it) on a laptop and I can't get to my regular ISP SMTP mail server when I am not on my home Internet connection because Roadrunner blocks port 25.  I need to be able to send email when I am at the airport or at a hotel on the road.  I have searched the forums and haven't found anything about this specifically but I think I have learned enough to know I need a local SMTP relay server installed on my laptop.  I want to use Thunderbird as the client to send and receive email (already have it loaded and it will fetch emails).

Can someone please confirm that I need a local SMTP server and tell me some simple package in the repositories to install (or is there something that was already installed as part of Dapper?).  There is freeware available for Windows that will do something like this but I haven't seen anything for Ubuntu so far.

(OK....it's probably a dumb question that everyone else knows the answer to but that's why I posted it here.)

Thanks in advance for any assistance.

---

### Post by bswilson on 2006-10-09
> **phalon said:**
> I can't get to my regular ISP SMTP mail server when I am not on my home Internet connection because Roadrunner blocks port 25.

Uh, you sure about that?  I have Road Runner with Thunderbird configured to use smtp-server.nc.rr.com, and there are no problems.

---

### Post by gn2 on 2006-10-09
I just use Webmail myself when I'm away from home...

---

### Post by phalon on 2006-10-09
Oops....actually that's my wife's provider......I meant to say the outgoing email server is smtp.ev1.net.  I can fetch email but I can't send it.  When I attempt to telnet to the server (telnet smtp.ev1.net 25) the connection times out.  When I connect to the roadrunner account, I get a connected message so it's not blocked.

---

### Post by dca on 2006-10-09
Are you using an email client to send your email from an airport or wherever?  For instance, some people I know who are consultants config their client to use their native POP3/SMTO servers for their particular ISP.  When they go to a client's organization and configure their laptop to use their network (for an internet connection) the email client stops sending emails.  This instance is because the firm they are consulting blocked activity on port25 unless it goes to their SMTP...  The only solution was to use a WebMail based client...

---

### Post by phalon on 2006-10-09
I am using Thunderbird and I can't connect to the Ev1 smtp server from an airport or a hotel if I use the same server information I use at home because they block port 25 for everything but dial up connections to their network.  I thought a local smtp server running on my laptop might let me send from any Internet connection.

---

