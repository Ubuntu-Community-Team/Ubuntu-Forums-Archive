---
title: "help with the big one... emails!"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by napi on 2008-03-18
Hi all,

Am a small-time freelance web designer, and have gotten sick of searching around for web hosts for sites I do, so figured it's about time I get my own server going. (That and it's *definately* about time I try out linux having been on windows machines all my life).

Installed Ubuntu Server, then did apache/mysql/php manually (good learning experience setting them all up).

That stuff, with the helping hand of good documentation went very smoothly.

So now I'm at the email part of the whole thing. Now I'm well aware that email stuff can take a lot of setting up and, as I'm not a fan of just following a "setup guide" I'm trying to understand it all as I go along by working a lot of it out for myself.

However,

I'm struggling with MX records and what sort of email setup to go with.

I have several domains that all point to the same server. To save resources, I'm not running my own nameservers, but using the ones provided by 123reg (who I registered the domains with).

The DNS to get the domains to go to the server work fine.

However, not quite sure how MX records work - do I need to point them at my server? use the 123reg ones? Can't find much about what to do with them.

Similarly what type of setup on the server itself should I go for? I like the Maildir/ setup, as I give a (limited) shell access to some of my clients, and want to provide imap and (eventually) Squirrelmail. I handle the multiple domains with virtualhosts, and have seen in the postfix documentation I can do virtual email accounts as such.

Any help/advice is greatly appreciated.

- napi

---

### Post by hyper_ch on 2008-03-18
just two thigns:

(1) if you want to operate a real mail server you need a static IP

(2) if you want to setup a webserver with email and so on, I'd use the perfect howto over at [http://www.howtoforge.com](http://www.howtoforge.com)  --> it is easily done copy'n'paste and you end up with a ISP-style setup (meaning you can host multiple websites and email....)

---

### Post by Oldsoldier2003 on 2008-03-18
[http://publib.boulder.ibm.com/infocenter/iseries/v5r3/index.jsp?topic=/rzakk/rzakkconceptbasic.htm](http://publib.boulder.ibm.com/infocenter/iseries/v5r3/index.jsp?topic=/rzakk/rzakkconceptbasic.htm)

A very in depth writeup on DNS . There are also examples of MX records in there, but since you said you like to understand, I thought this resource could help you.

---

### Post by napi on 2008-03-18
Have got a static ip,

Have read through that howto guide on the 'perfect server'

A lot of it was very useful, but I don't want to use ISPConfig (seems a bit heavy-handed for what I'm doing)

And it doesn't really explain what what you're doing or why you do half of it.

Difficulty I'm having is that some clients (and friends) will have shell accounts and some won't - trying to find a solution that accomodates both

---

### Post by hyper_ch on 2008-03-18
there are more tutorials on there... also hosting virtual email accounts (all data stored in databases)

---

