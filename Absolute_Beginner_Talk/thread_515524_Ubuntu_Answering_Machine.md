---
title: "Ubuntu Answering Machine?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Tixer on 2007-08-02
I get alot of telemarketers, and I want to put an end to them. I have 2 Feisty Fawn servers, and a stack of voice modems laying around (I'm sure one of them works). 

My idea is this: Splice the phone cord going to my room, crimp 2 ends on it, and run both through a voice modem. I want a way to filter what comes in, for example, by caller-id, or by line, or even by time of day. It would be so nice to say, filter all calls between 10 PM and 12 PM, on the phone in my room, so I wouldn't be woken up by someone selling me a mastercard, or stop the ring if it's someone I don't want to talk to.

I understand the drawback that if the power went out, I'd have no phone in my room, but I don't care.

Is this possible? Any drawbacks? What software is needed? Can it kill a kitten?

---

### Post by anewguy on 2007-08-02
Did you ever put your phone number on the do-not-call list?

---

### Post by Tixer on 2007-08-02
It isn't just telemarketers, and Canada doesn't have a DNC list yet. There are sometimes people I really don't want to talk to, or there are times I don't want to talk to them. I don't want to be woken up by a phone ringing, or have say, my mom's friends reaching my room.

---

### Post by silent1643 on 2007-08-02
sounds a little extreme to me, but im sure its possible 

"I want a way to filter what comes in, for example, by caller-id, or by line, or even by time of day."
-sound like you need to do some programming for this

[google]("http://www.google.com/search?client=opera&rls=en&q=linux+answering+machine&sourceid=opera&ie=utf-8&oe=utf-8") is always a good start :D

---

### Post by Tixer on 2007-08-02
Ugh, programming. I know I might not get all the features without tons of effort, but I'd think there's a way to screen calls using a program on Linux. For example:

Machine rules are set: (no calls between 10 PM and 12 PM, censor one ring, no 1800 numbers can call in, certain friends, etc)

Call comes in, machine censors the first ring (phone in my room doesn't ring until caller ID is there. If caller ID is good, it rings, if it's on the blacklist, it doesn't ring.)

You'd think there's a way to do that, no?

---

### Post by anewguy on 2007-08-06
> **Tixer said:**
> It isn't just telemarketers, and Canada doesn't have a DNC list yet. There are sometimes people I really don't want to talk to, or there are times I don't want to talk to them. I don't want to be woken up by a phone ringing, or have say, my mom's friends reaching my room.

Sorry - didn't know you were in Canada!:)

---

### Post by anewguy on 2007-08-06
Okay, this may sound a little strange, and I don't know if it would work or not, but.........

try searching for linux pbx software.  It's possible it may allow you to set up filters, rules, etc., as you want.

Here's a couple of posts I found:

[http://packages.ubuntu.com/feisty/comm/asterisk]("http://packages.ubuntu.com/feisty/comm/asterisk")

[http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu]("http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu")

I know it sounds like overkill, but here's the thing - you don't have to have a bunch of lines, etc., to use the software, and I think some sort of PBX software will provide you with some of the flexibility you are looking for.

Good luck, and be sure to let us know how things go!:)

---

### Post by hyper_ch on 2007-08-06
Asterisk is the way to go... it's also used in some professional support centers and guess what: It's free ;)

---

