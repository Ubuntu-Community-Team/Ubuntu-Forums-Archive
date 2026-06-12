---
title: "[SOLVED] Postfix, SASL, TLS, remote access"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by drhiii on 2008-03-01
I've made some cuts at this with The Perfect Installation, and some other tutorials, but am not getting a proper installation.  Am looking to see if anyone could point to a HOWTO or a tutorial that would work the following requirements.  Note that I am a n00b at this so please don't yell at me if this is old, old news.  Am learning, and I do listen:

Trying to set up a server that allows incoming, outgoing mail.  Very small group of users.  Clients range from Ubuntu's Evolution to Opera to Mozilla to Outlook.  Most of these people are in separate locations, meaning they are not on the same netblock.  Coming from everywhere.  So the need is for them to be able to connect from mobile locations, authenticate, and be able to relay email out to everywhere else.  And visa versa.  Also, there are more than on domains to be handled by this installation.

I got things resonably working, but I seem to have a problem with Outlook clients, and also incoming email does not always make it in.  Rather than post reams of logs, would like to try from scratch with a recommended tutorial that would provide for these simple things above.

tx

---

### Post by zazuge on 2008-03-02
well that depands on your network
do you have a sattic IP or a MX record
are your connecting via dialup?
are your using DSL to access the NET?
are you behind a firewall/Proxy/NAT ?

in the case of you having a MX record that postfix will work fine alone
if you don't then you need a pop client like fetchmail
for your users to access the mail server you need some pop server or a webmail like squirelmail 

hope that helps.

---

### Post by drhiii on 2008-03-02
Hello,

I have never received instant notification from here so am delayed in responding.

Fortunately, I finally did break the ice and get a working setup late last eve.  So I can mark this thread as solved.  I appreciate your response to this however.  I won't have to scrape my way to a working setup however, having arrived at a solution last eve.

tx, drh


> **zazuge said:**
> well that depands on your network
do you have a sattic IP or a MX record
are your connecting via dialup?
are your using DSL to access the NET?
are you behind a firewall/Proxy/NAT ?

in the case of you having a MX record that postfix will work fine alone
if you don't then you need a pop client like fetchmail
for your users to access the mail server you need some pop server or a webmail like squirelmail 

hope that helps.

---

