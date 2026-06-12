---
title: "ofx direct connect"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by tsgray on 2007-10-11
I've just spent the past 6 hours trying to get any financial software package to use ofx to directly connect to my accounts. I'd prefer to use kmymoney but the package in synaptic doesn't have ofx enabled and I have no idea how to even begin compiling from scratch. Does anyone have a link to a package with ofx support built in. If someone can give me steps to compile I'm willing to give that a shot as well. I'm running feisty on an amd64.

Thanks

---

### Post by mndzmyst on 2007-10-19
Don't know much about kmymoney, but I just got gnucash to connect with my bank online using ofxdirectconnect. If you're interested the link is below.

[http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)

I'm using gutsy and all was the same. Except for user name, for which I had to use the actual name on the account as it would not connect otherwise. Also, make sure to include the  --enable-hbci flag, since it provides aqbanking support which you will need.

---

