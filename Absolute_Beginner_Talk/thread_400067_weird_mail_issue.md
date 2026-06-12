---
title: "weird mail issue"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-04-03
i have been using opera's email client with my road runner account, with no problem. yesterday, i started getting these 5.7.1 errors when trying to send mail through the smtp server. i tried a bunch of things, including installing sylpheed-claws and thunderbird, but still got the same. my wife is not having trouble on our old desktop with the same account, but i'm not sure what she's tried (i'm travelling). adding to the oddity, i can send mail just fine from this account from within my gmail account. i'm clueless.

---

### Post by heimo on 2007-04-03
Hmm... 5.7.1 unable to relay? Can you add username and password to your outgoing (smtp) settings in the mail client? Do you use mail server that is from you ISP? Check this:
[http://kb.mozillazine.org/5.7.1_Unable_to_relay](http://kb.mozillazine.org/5.7.1_Unable_to_relay)

---

### Post by fuscia on 2007-04-03
> **heimo said:**
> Hmm... 5.7.1 unable to relay? Can you add username and password to your outgoing (smtp) settings in the mail client? Do you use mail server that is from you ISP? Check this:
[http://kb.mozillazine.org/5.7.1_Unable_to_relay](http://kb.mozillazine.org/5.7.1_Unable_to_relay)

i saw that when i installed thunderbird (which i've since uninstalled). as this is going on with opera mail and sylpheed-claws, but not my gmail account on this computer and not with my wife on another computer (thunderbird on breezy), with the same account, i'm thinking this has something to do with something i must have done to this one (wouldn't be the first and won't be the last problem i've ever caused). about a week ago, i was messing with sendmail (and i didn't know what i was doing) trying to get sending on pine to work (i gave up pretty quickly, though and uninstalled it). this is, more and more, looking like a classic case of 'user error'.

btw, that was a great idea about adding another account to the mail client to see what it would do. i used another road runner account and that had the same problem with the opera client while working in my gmail account. so, it's not specific to my regular account, i would assume.

---

### Post by mikeyphi on 2007-04-03
> **fuscia said:**
> i saw that when i installed thunderbird (which i've since uninstalled). as this is going on with opera mail and sylpheed-claws, but not my gmail account on this computer and not with my wife on another computer (thunderbird on breezy), with the same account, i'm thinking this has something to do with something i must have done to this one (wouldn't be the first and won't be the last problem i've ever caused). about a week ago, i was messing with sendmail (and i didn't know what i was doing) trying to get sending on pine to work (i gave up pretty quickly, though and uninstalled it).

When you uninstalled the trial programs it's possible that some files didn't get removed. You might do a search on the (program) name and remove the offending items!  Perhaps after that you will be able to operate your original emailer...

---

### Post by fuscia on 2007-04-05
> **mikeyphi said:**
> When you uninstalled the trial programs it's possible that some files didn't get removed. You might do a search on the (program) name and remove the offending items!  Perhaps after that you will be able to operate your original emailer...

looks like that did it. there was an /etc/mail thing and two leftovers from sylpheed-claws. getting rid of them did the trick, although i have no idea why.

---

