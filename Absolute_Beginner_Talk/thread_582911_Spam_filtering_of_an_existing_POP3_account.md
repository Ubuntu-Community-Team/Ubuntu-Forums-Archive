---
title: "Spam filtering of an existing POP3 account"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by RazerDad on 2007-10-20
Hi, I'm converting from WIndows and the last thing on my list is email.

I currently have several POP3 accounts with my ISP (1 per family member).  I use MailwasherPro to log into these accounts and clean up any spam. I then run up outlook and download the cleansed mail.

It's a bit clunky but I've gotten used to it. 

I suppose, in an ideal world, I'd like some software to sit between my mail client (I haven't decided between evolution or Thunderbird yet) and remove spam before I see it. 

I searched for a spam mail filter on ubuntu and had several posts mentioning spamassassin and postfix. I assume that spamassassin is the tool which will clean up my mail. Not sure what postfix provides.. 

I'm sure there's a newbie guide to setting stuff up like this as email is one of the top "must haves", but I can't find a suitably janet & john guide to setting it up.

Thx
Mark.

---

### Post by mikeyphi on 2007-10-20
I use spamassassin with Evolution - the spam and a few good emails!! are filed in the junk folder - so I have to check in there! but it does keep my inbox clear!!!
I haven't heard of anything like mailwasher to clean your emails before downloading.

---

### Post by thelocust on 2007-10-20
I would go with thunderbird evolution spam filters don't seem to work to well. And thunderbird has one pissed off spam filter when I tried it on window it sucked but on linux it works for some reason. When I first fired it up I had to go and tell it what wasn't spam. I think that spamassasin is a plugin for thunderbird to.

---

### Post by RazerDad on 2007-10-20
OK, so all i need now is someone to guide me through installing and setting up spamassassin.

I'm technical, to a point, but i don't want to muck about to much with my email as it's my lifeblood (which is also why it's the last thing on my list to convert).

from reading a couple of other post, I think I understand that postfix is a mail "acquirer". i.e. it is responsible for connecting to my pop3 accounts. It would then forward this mail (somehow) to spamassasin for spam detection and then onto my mail client.

I can see one flaw with this in that it appears that I have to download the offending spam before it can be removed. Ideally I'd like something to check directly on the pop3  server and pinpoint spam and delete it there, saving me from having to download it.

I could really do with this being relatively seamless and painless ..

---

### Post by mikeyphi on 2007-10-20
System/Administration/Synaptic Package Manager
enter 'spamassassin' in search field
right click/mark for installation - apply

all done!!

Can't speak for Thunderbird but under Evolution there is a junk folder- you can set the options for when this gets emptied and you can indicate non-junk mail which is then transferred to the inbox.

---

### Post by RazerDad on 2007-10-20
OK, the installation bit is easy. I'd worked that out myself. It's the setup of it which appears daunting...

How do I get spamassassin to clean my pop3 accounts etc.

---

### Post by drinkpepsi on 2007-10-20
[http://freshmeat.net/projects/testmail](http://freshmeat.net/projects/testmail)

---

