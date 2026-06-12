---
title: "Setting up Mail Server?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-01-25
I was wonder what I would have to do to setup a mail server...

for example... i have a server with my website on it. lets say my domain was [www.rob.com](www.rob.com)

if i wanted to setup mail so it was like "rob@rob.com"... how would i go about doing this?

i am pretty new to this, thanks for the help!

---

### Post by kidders on 2007-01-26
Hi there,

Doing that yourself is not a trivial undertaking, in that you would have to have a computer up (and properly accessible) 24/7.

The theory is simple enough though:

[LIST=1]
[*]Set up an SMTP gateway (eg Postfix).
[*]Install something to let users check their mail (eg Courier IMAP w/ SSL).
[*]Do lots of testing.
[*]Create an MX record in your DNS, pointing to your mail server (so other SMTP servers know where to route mail destined for your domain).
[*]Set up spam filtration (eg Spamassassin).
[*]Set up virus protection (eg ClamAV).
[/LIST]
My setup is somewhat similar to what I've described. If you intend to use addresses hosted by your mail server for important things (ie something other than mailing your mates!), I very strongly recommend purchasing a backup MX service (such as that provided by DynDNS.com) to handle mail when (and I mean when!) your server goes down, or becomes inaccessible for some reason. Bear in mind that some of these reasons may have nothing to do with you, such as a communications failure between two continents, etc.

I suppose step 7 is to read about the SMTP protocol, so you can learn stuff like:

[LIST]
[*]How to reliably detect spam or DoS attacks.
[*]How mail servers typically behave when something goes wrong on your gateway.
[*]What you can/can't expect other SMTP gateways to do for you.
[*]Etc.
[/LIST]

If you already know this much, and were hoping for something more detailed, let me know!

---

### Post by MrHorus on 2007-01-26
> **kidders said:**
> 

[LIST=1]
[*]Set up an SMTP gateway (eg Postfix).
[*]Install something to let users check their mail (eg Courier IMAP w/ SSL).
[*]Do lots of testing.
[*]Create an MX record in your DNS, pointing to your mail server (so other SMTP servers know where to route mail destined for your domain).
[*]Set up spam filtration (eg Spamassassin).
[*]Set up virus protection (eg ClamAV).
[/LIST]

I'm not prepared to give anyone free advertising, but at the moment I pay a US-based hosting company $15pm for a virtual server and I run everything on that.

First thinf you want to do is set up the DNS for your domain rob.com and once the DNS has propagated and your server is answering for the domain, point the MX record at your server so the domain's email will look there.

Then, install the mail server and delivery agent - I use exim and procmail with the mailboxes being IMAP format.

```
apt-get install exim4 procmail courier-imap
```

Debconf should prompt you to set it up and you want it to accept mail relaying for your domain and localhost.

After this, I would read a good guide to configuring IMAP mailboxes (I used the Maildir format) and then how to securely encrypt the connection with SSL so that passwords are not sent in plaintext - courier-imap-ssl is the package you would want for this.

It's *is* a little daunting to set up the first time but there are plenty people here who can help if you need advice :)

---

### Post by hyper_ch on 2007-01-26
Just one thing:

DO NOT RUN A MAILSERVER FROM A NON-DEDICATED IP ADDRESS!

Most server will refuse connection to and from a server which has a dynamic ip address.

However you may want to have a look here:


[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

[http://www.howtoforge.com/taxonomy_menu/1/78](http://www.howtoforge.com/taxonomy_menu/1/78)

---

### Post by MrHorus on 2007-01-26
> **sjau said:**
> 
DO NOT RUN A MAILSERVER FROM A NON-DEDICATED IP ADDRESS!

Most server will refuse connection to and from a server which has a dynamic ip address.


It's more an issue with the lack of proper reverse DNS delegation and as sjau said, many servers will bounce email if it cannot resolve the reverse DNS.

---

### Post by tim.n9puz on 2007-01-26
I've been working on an mail server as well to learn more about them.

Presently, with postfix installed I can send email from an account on the server to anywhere in the "outside" world. From anywhere else I can send email to "tim@timscomputer.org" and it arrives in the accounts mailbox on the server.

However, if I am at my regular home computer and I try to send an email using the "tim@timscomputer.org" account the client (Thunderbird) gives an error that reads "Relay access denied." In searching here and elsewhere this seems to be a common error. Lots of people write about it but there doesn't seem to be a straightforward answer about what configuration needs to be changed.

Eventually I'd like spam reduction, anti-virus, etc. but I'd like to add things one piece at a time to better understand what does what. I am only running postfix right now without any pop or imap services, etc. I believe this will not let me retrieve any email externally but that's okay at this step unless my thinking of trying to keep it very simple is flawed.

I'll admit I'm new to email systems but this seems like sending an email through the server from another computer is an obvious thing to want to do with an email server.

Thanks for any pointers or advice.

Tim

---

### Post by kidders on 2007-01-26
Hi there,

> **tim.n9puz said:**
> if I am at my regular home computer and I try to send an email using the "tim@timscomputer.org" account the client (Thunderbird) gives an error that reads "Relay access denied."

Think of this in terms of how you would like your mail server to react under the following circumstances:

[LIST]
[*]Some disenchanted guy happens accross an open port 25 on your server.
[*]He decides to try to use it to launch a DoS attack on his local government.
[*]He's already found 9 willing SMTP gateways, and he wants to know if yours can be #10.
[*]He tries to send a mail from one hotmail account to another via your gateway.
[/LIST]

Naturally, you will have configured your server never to accept email destined for a non-local address, unless it is coming from a local IP. That way, your SMTP gatway can never be used to forward (relay) mail that it is neither the final destination for, or original source of.

Of course, as you've noticed, this gets in the way of your own legitimate use of your own server. Whenever you're not on the server's local network, you get treated like a spammer! One possible solution (the one I use) is to enable secure SMTP and set up authentication, much like you would with IMAP. You could then safely allow authenticated users to break relaying rules, with the added bonus of encryption.

> **tim.n9puz said:**
> Eventually I'd like spam reduction, anti-virus, etc. but I'd like to add things one piece at a time to better understand what does what.These are quite straightforward things to do, really. You will notice that there are two main types of HOWTOs on the subject, though:

[LIST=1]
[*]Ones that involve running multiple SMTP servers, possibly on the same machine. This tends to be a tremendously robust configuration, designed to be as asynchronous as possible.
[*]Ones that simply configure postfix to pipe mails through binaries, much like you do when you type something like **dmesg | tail** on your console.
[/LIST]

Before you set up spam/virus protection, you should maybe read a little about the two approaches, just so you are aware of which one the HOWTO you choose to follow is using. Tbh there is very little difference between them in terms of set-up difficulty.

Hope that helps.

---

### Post by tim.n9puz on 2007-01-26
> **kidders said:**
> Hi there,

Think of this in terms of how you would like your mail server to react under the following circumstances:

[LIST]
[*]Some disenchanted guy happens accross an open port 25 on your server.
[*]He decides to try to use it to launch a DoS attack on his local government.
[*]He's already found 9 willing SMTP gateways, and he wants to know if yours can be #10.
[*]He tries to send a mail from one hotmail account to another via your gateway.
[/LIST]


Yes. I definitely want to prevent this situation.

> **kidders said:**
> 

Naturally, you will have configured your server never to accept email destined for a non-local address, unless it is coming from a local IP. That way, your SMTP gatway can never be used to forward (relay) mail that it is neither the final destination for, or original source of.

Of course, as you've noticed, this gets in the way of your own legitimate use of your own server. Whenever you're not on the server's local network, you get treated like a spammer! One possible solution (the one I use) is to enable secure SMTP and set up authentication, much like you would with IMAP. You could then safely allow authenticated users to break relaying rules, with the added bonus of encryption.


Are you refering to the TLS options here?

> **kidders said:**
> 

These are quite straightforward things to do, really. You will notice that there are two main types of HOWTOs on the subject, though:

[LIST=1]
[*]Ones that involve running multiple SMTP servers, possibly on the same machine. This tends to be a tremendously robust configuration, designed to be as asynchronous as possible.
[*]Ones that simply configure postfix to pipe mails through binaries, much like you do when you type something like **dmesg | tail** on your console.
[/LIST]

Before you set up spam/virus protection, you should maybe read a little about the two approaches, just so you are aware of which one the HOWTO you choose to follow is using. Tbh there is very little difference between them in terms of set-up difficulty.

Hope that helps.

Every little bit helps. I'm an embedded systems programmer by trade and part time sysadmin out of necessity. The ins and outs of an email server don't seem like they are overly complex but the documentation sure seems difficult to get your mind around the first time out. Perhaps because there are so many options to choose from.

Thanks for the help. I will look into the things you've discussed.

Tim

---

### Post by kidders on 2007-01-26
> **tim.n9puz said:**
> Are you refering to the TLS options here?Yep, sorry... I should've been more specific. You should leave anonymous, unencrypted SMTP available as well though. The idea would be that having the option of authenticating would let you violate relaying restrictions on demand.

I suppose, for the sake of completion, I should also have pointed out that you can whitelist hosts for relaying by IP, too. Of course, that's only useful if you typically access your mail server from a static IP, and ... well ... it's a bit hacky, imo. It would be far quicker to implement though (<30 seconds).

> **tim.n9puz said:**
> the documentation sure seems difficult to get your mind around the first time out.That's certainly true! If you run into something specific you are having trouble with, you should post it ... As I'm sure you know, making mistakes with mail servers is easy.

You may already know this too, but if you're experimenting with something new, always remember to switch on soft bouncing. That way, an accidental error won't cause you to lose mails. (Soft bounces are error codes in the 4xx range.)

---

