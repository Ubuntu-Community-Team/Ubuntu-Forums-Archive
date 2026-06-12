---
title: "no host found"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by lex1 on 2007-12-24
set up a mx record for som.nymdomain.net as a virtual domain but when i sent mail it comes back <someone@som.mydomain.net>:
 <bliss_> Sorry,_I_couldn't_find_any_host_named_son..mydomain.net._(#5.1.2)/


lexq

---

### Post by blueridgedog on 2007-12-24
Are you trying to host DNS services for son.mydomain.net and setup an MX record that points to your own host for testing?

Give me more of an idea of what you are trying to do.

Read the man page for dig.  Dig can be used to "dig" your own DNS or other DNS records (even in a test setup) to find problems.  So if you are testing DNS you can dig @localhost

---

### Post by ~LoKe on 2007-12-24
Are you sure you have it configured properly?  In the three instances where you name the domain, you've written it differently.

> set up a mx record for **som.nymdomain.net** as a virtual domain but when i sent mail it comes back <someone@**som.mydomain.net**>:
<bliss_> Sorry,_I_couldn't_find_any_host_named_**son..mydomai n.net**._(#5.1.2)/

Not sure if that's the problem, but it stands out...

---

