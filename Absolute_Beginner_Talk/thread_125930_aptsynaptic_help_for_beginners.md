---
title: "apt/synaptic help for beginners"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by creutz on 2006-02-05
hello all newbies (like me)

I got these kind of error messages;
 - Could not connect to security.ubuntu.com:80
 - Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy/breezy-scurity
and searched for help.
I tried with different proxies but no good.
Finally I got the idea to check the Authentication keys, because it was only the security branch that was not working.
After first deleting and then resetting the Authentication keys everything started to work.

start Synaptic
click Settings, Repositories
click Authentication
click Restore default keys
click Close
click OK

that's it

So hopefully this is of use for someone (like me).

Now I believe in Ubuntu again :)

creutz

---

