---
title: "MacBook wifi half-works"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by boumcke on 2006-09-17
Hello,

I bought a Macbook, simplest version, and I'm having a really strange problem. I read quite a few posts about the wifi case on the Macbooks, and I know the answer to my question might be to wait for a new version of the driver, but anyway I want to risk it.

The problem is the following : my interface ath0 is up, and I can ping whatever site I want. But strangely I can't access any website I haven't ping-ed before, ie. if I want to access google I have to ping [www.google.com](www.google.com) first, or if I want to check my GMail account using a mail client, I have to ping pop.gmail.com .
Either there's something I completely missed when I set up my connection, or I definitely don't understand what's happening.

I set up my connection using the following commands :

iwconfig ath0 essid XXX
iwconfig ath0 key XXX
dhclient ath0

Is there something more to do ? I'm completely lost. It's really annoying. If someone has an idea, or just wants to say a word to recomfort me, that would at least make me feel a little bit better...:confused:

---

### Post by boumcke on 2006-11-13
Ok, it turns out it was simply a DNS problem. Still don't know what happens though, apparently the router isn't transmitting correctly the DNS servers addresses. I had to put it manually into /etc/resolv.conf and now it works correctly.

---

