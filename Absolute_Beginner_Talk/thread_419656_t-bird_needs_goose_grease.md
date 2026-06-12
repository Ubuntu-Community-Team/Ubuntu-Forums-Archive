---
title: "t-bird needs goose grease"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by rgp-02 on 2007-04-23
just installed 7.04 & XP (dual boot) on a clean hard drive and all is well....

except...

i can't get my t-bird mail receive (hotmail.com) service to function; sending mail functions well.

tried using the same settings i had with t-bird in ubuntu 6.10, but it wont work:

server type: POP
server name: localhost	
username: [email]username@hotmail.com[/email]

any humiliating suggestions?

---

### Post by RobsterUK on 2007-04-23
What error are you getting?

---

### Post by rgp-02 on 2007-04-23
Alert

  !  Could not connect to server localhost; the connection was refused.

---

### Post by nhandler on 2007-04-23
Using a server of localhost will only work if you have an smtp server running on your computer.

---

### Post by rgp-02 on 2007-04-23
these are the settings i used with t-bird on ubuntu 6.10:

SERVER SETTINGS (RECEIVE):

server type: POP
server name: localhost	
username: [email]username@hotmail.com[/email]

OUTGOING SERVER (SMTP) SETTINGS:

description: not specified
server name: [email]mail@optonline.net[/email]	
port:25
user name: [email]username@hotmail.com[/email]
secure coneection: none

....they worked.....

---

### Post by rgp-02 on 2007-04-23
c'mon now guys.....

i need one of you i.q. skyrocketing, rocket scientist type megagenius einsteins (frankensteins need not apply) to save my day before my wife has me put in the mental hospital again.......and it's too nice a day for that!

let's go, let's go, LET'S GO!

i need answers!

---

### Post by igknighted on 2007-04-23
> **rgp-02 said:**
> c'mon now guys.....

i need one of you i.q. skyrocketing, rocket scientist type megagenius einsteins (frankensteins need not apply) to save my day before my wife has me put in the mental hospital again.......and it's too nice a day for that!

let's go, let's go, LET'S GO!

i need answers!

PLEASE, only bump after 24 hours... we do patrol the back pages for posts that slip through... and a simple bump suffices, theres no need to mock anyone like that either.

As for your question, you need to look up from hotmail what the settings should be.  They should have some sort of how-to there for setting up thunderbird.  Also, try to use imap instead of pop if it is offered... pop is older and once you download to your computer the mail is no longer available online (I found this out by losing 2+ years of mail a few months ago because I accidentally used pop over imap)

---

### Post by dreadlord_chris on 2007-04-23
> **rgp-02 said:**
> just installed 7.04 & XP (dual boot) on a clean hard drive and all is well....

except...

i can't get my t-bird mail receive (hotmail.com) service to function; sending mail functions well.

tried using the same settings i had with t-bird in ubuntu 6.10, but it wont work:

server type: POP
server name: localhost	
username: [email]username@hotmail.com[/email]

any humiliating suggestions?

How about this one: You need to install whatever pop3 proxy app you were using under 6.10 to be able to receive **any** Hotmail emails from _localhost_.

You do realize that _localhost_ is your *own* computer don't you?

Maybe it was [Hotway]("http://sourceforge.net/projects/hotwayd/")?

---

### Post by dreadlord_chris on 2007-04-23
> **igknighted said:**
> Also, try to use imap instead of pop if it is offered... pop is older and once you download to your computer the mail is no longer available online (I found this out by losing 2+ years of mail a few months ago because I accidentally used pop over imap)

Or you could set your pop3 client to leave emails on the server. Pretty sure all the pop3 clients I've used have had this option. Usually there is also an option to delete emails from server when they are deleted locally.

---

### Post by rgp-02 on 2007-04-23
in 7.10 (t-bird) there are no options for pop3 or imap; only pop...

...also, i couldn't find any “how-to's” or info for settings at hotmail

---

### Post by dreadlord_chris on 2007-04-23
> **rgp-02 said:**
> in 7.10 (t-bird) there are no options for pop3 or imap; only pop...

...also, i couldn't find any &#8220;how-to's&#8221; or info for settings at hotmail

pop == pop3

And you're probably not gonna find any how-to's at Hotmail for setting up email clients - simply because, by design, Hotmail is only accessible through the Hotmail web site. This is why I said you need to install a pop3 proxy. The proxy would run on your computer (localhost), listening for pop3 requests from your email client (TB). It translates these pop3 commands into the proper HTTP requests and sends them on too Hotmail, then receives and translates the HTTP responses into pop3 for your email client.

---

### Post by rgp-02 on 2007-04-23
ok....how do we do the “install a pop3 proxy” thing?

---

### Post by dreadlord_chris on 2007-04-23
> **rgp-02 said:**
> ok....how do we do the &#8220;install a pop3 proxy&#8221; thing?

did you actually set up your computer when you were running 6.10? Because you **have** to have been using one to have accessed your Hotmail from TB.

Anyway - didn't you see the link I posted to Hotway - [http://sourceforge.net/projects/hotwayd/](http://sourceforge.net/projects/hotwayd/)

It's also in the repositories....

---

### Post by rgp-02 on 2007-04-23
THAT'S IT!

thanks for all replies but i don't have any more time to waste on this. i'll just access it from hotmail.

---

### Post by rgp-02 on 2007-04-24
[QUOTE=rgp-02;2517042]in 7.10 (t-bird) there are no options for pop3 or imap; only pop...

..and it looks like i was wrong about that too!

after putzing around with it this morning, i found i CAN set imap

....but it does not work either.

---

### Post by ceeg on 2007-04-24
Try this thunderbird extension maybe,

[http://www.extensionsmirror.nl/index.php?showtopic=2518](http://www.extensionsmirror.nl/index.php?showtopic=2518)

---

### Post by rgp-02 on 2007-04-24
ok, i downloaded extension

now how do i install it?

---

### Post by rgp-02 on 2007-04-24
so....i went to [http://sourceforge.net/projects/hotwayd/](http://sourceforge.net/projects/hotwayd/)

and i found about a hundred or so different options to choose from!

which one do i pick?    and

how do i install it?

---

### Post by rgp-02 on 2007-04-24
Well?

Where is everybody?……...what happened to all the einsteins?

You guys are real good at telling WHAT to do

But when it comes to HOW to do , you’re nowhere to be found!

You can talk the talk, but can’t walk the walk!

Thanks, I’ll figure it out myself.

Good night.

---

### Post by dreadlord_chris on 2007-04-25
> **rgp-02 said:**
> Well?

Where is everybody?&#8230;&#8230;...what happened to all the einsteins?

You guys are real good at telling WHAT to do

But when it comes to HOW to do , you&#8217;re nowhere to be found!

You can talk the talk, but can&#8217;t walk the walk!

Thanks, I&#8217;ll figure it out myself.

Good night.

Gee, I'm sorry....would you like someone to come over and install it for you?

---

### Post by thegreenman on 2007-04-25
> **dreadlord_chris said:**
> Gee, I'm sorry....would you like someone to come over and install it for you?

Jeeze some people expect the world from a forum of volunteers. Sheesh. That guy needs some decaf and a few hours on hold with M$ tech support to get his expectations in order.

---

### Post by ceeg on 2007-04-27
> **rgp-02 said:**
> ok, i downloaded extension

now how do i install it?

Did you try reading the documentation?
[http://webmail.mozdev.org/faq.html](http://webmail.mozdev.org/faq.html)

---

