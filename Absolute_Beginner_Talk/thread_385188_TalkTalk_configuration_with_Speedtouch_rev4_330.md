---
title: "TalkTalk configuration with Speedtouch rev4 330"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Docter on 2007-03-15
Those on talktalk ADSL might want to set their options either in /etc/ppp/options or /etc/ppp/peers/(dsl provider/modem name) (example mine is in: /etc/ppp/peers/speedtch):

noipdefault
noauth
usepeerdns
noccp
noaccomp
nopcomp
novj
mru 1400

lcp-echo-interval 0
lcp-echo-failure 0

and if you aregetting proxyarp errors in debug.log then edit the line in /etc/ppp/options from:

proxyarp

to

noproxyarp

It's a good idea to turn the debug option on in your options file and read the log hunting for "ConfRej" being sent to you, this is slowing down your dial in while the LCP is being negotiated so look to disable the request in the first place by using the options file you're altering. ( type "man ppd" at a terminal and look atthe options available).

Thanks to the configurability of linux I have a more stable connection with my rev 4 speedtouch 330 USB than I ever did with XP.

In your eye Gate$.


It's taken me the best part of a week to install two ubuntus on a crossover connection sharing an internet connection, but I feel I've learned a fair bit and so I offer what help I can. This is my first experience with linux and XP is already a distant memory.

---

