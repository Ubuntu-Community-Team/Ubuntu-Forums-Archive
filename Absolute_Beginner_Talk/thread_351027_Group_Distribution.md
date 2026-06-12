---
title: "Group Distribution"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Tspiritstorm on 2007-02-01
In postfix/mysql I am trying to create alias accounts for my users. However it seems I misunderstood what everyone is calling an alias. 

For example lets say I am trying to have [email]admin@mydomain.com[/email] in name only but any email that goes to [email]admin@mydomain.com[/email] really delivers to [email]myname@mydomain.com[/email].

It seems alias or forward works externally only. How can I create internal aliases like above?

---

### Post by Tspiritstorm on 2007-02-01
mysql seems to query SELECT destination FROM forwardings WHERE source= 'myalias@mydomain.com' and then it moves to the next query. 

When I do this query myself it displays the correct information:

SELECT destination FROM forwardings WHERE source='myalias@mydomain.com'

[email]myname@mydomain.com[/email]

So if it is finding this query why is it moving on to the next step??

---

